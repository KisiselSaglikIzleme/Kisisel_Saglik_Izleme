KAYDEDİLEN VEYA YENİ OLUŞRULMAK İSTENİLEN VERİLER İÇİN VERİ KOMUTLARI
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

MAİNACTİVTY.JAVA
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

import com.google.firebase.auth.FirebaseUser;
//MAİNACTİVTY.JAVA İÇERİSİNDE TANIMLANAN BU KOD GOOGLE VERİ TABANI İMPORT EDİLMESİNİ SAĞLAMAKTADIR.
************************************************************************************************************************************************************************

REGİSTERACTİVTY.JAVA
------------------------------------------------------------------------------------------------------------------------------------------------------------------------


import com.google.android.gms.tasks.OnCompleteListener;
import com.google.android.gms.tasks.Task;
import com.google.firebase.auth.AuthResult;
import com.google.firebase.auth.FirebaseAuth;

 private FirebaseAuth auth;
auth = FirebaseAuth.getInstance();

auth.createUserWithEmailAndPassword(email,password).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
            @Override
            public void onComplete(@NonNull Task<AuthResult> task) {
                if(task.isSuccessful()){

                    Intent LoginIntent =new Intent(RegisterActivity.this, Login.class);
                    startActivity(LoginIntent);
                    finish();
                }else;


//YUKARIDAKİ KOD KISIMLARI REGİSTERACTİVTY.JAVA CLASS IMIZIN İÇİNDE BULUNAN KOD PARÇACIKLARIDIR.
//BU KOD PARÇACIKLARI BİZİM YENİ KULLANICI OLUŞTURMAMIZI SAĞLAMAKTADIR.
*************************************************************************************************************************************************************************

LOGİN.JAVA
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

import com.google.android.gms.tasks.OnCompleteListener;
import com.google.android.gms.tasks.Task;
import com.google.firebase.auth.AuthResult;
import com.google.firebase.auth.FirebaseAuth;
import com.google.firebase.auth.FirebaseUser;


private FirebaseAuth auth;
private FirebaseUser currentUser;

auth = FirebaseAuth.getInstance();
currentUser = auth.getCurrentUser();


    private void loginUser() {
        String email=txtEmail.getText().toString();
        String password= txtPassword.getText().toString();
        if(TextUtils.isEmpty(email)){
            Toast.makeText(this, "email alanı boş olamaz", Toast.LENGTH_SHORT).show();
        }else if(TextUtils.isEmpty(password)){
            Toast.makeText(this, "şifre alanı boş olamaz", Toast.LENGTH_SHORT).show();
        }else{
            auth.signInWithEmailAndPassword(email,password).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
                @Override
                public void onComplete(@NonNull Task<AuthResult> task) {
                    if(task.isSuccessful()){
                        Toast.makeText(Login.this, "GİRİŞ BAŞARILI", Toast.LENGTH_SHORT).show();
                        Intent anaIntent = new Intent(Login.this, anaekran.class);
                        startActivity(anaIntent);
                        finish();
                    }else{
                        Toast.makeText(Login.this, "giriş başarısız", Toast.LENGTH_SHORT).show();
                    }
                }
            });

        }
    }


//YUKARIDAKİ KOD PARÇACIKLARI LOGİN.JAVA CLASS IMIZDA BULUNAN VERİTABANI İLE İLGİLİ KOD PARÇACIKLARIDIR.
//YUKARIDA TANIMLI OLAN FONKSİYONUMUZ BİZİM AKTİF KULLANICILAR ARASINDA GİRİŞ YAPMAYA ÇALIŞTIĞIMIZ KULLANICININ KONTROLÜNÜ SAĞLAMAKTADIR.
//KONTROLÜ SAĞLANAN KULLANICILAR İLGİLİ MESAJLARI ALIRLAR.

************************************************************************************************************************************************************************

ANAEKRAN.JAVA
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
import com.google.firebase.auth.FirebaseAuth;
import com.google.firebase.auth.FirebaseUser;

public class anaekran extends AppCompatActivity {
    private FirebaseAuth auth;
    private FirebaseUser currentUser;

    public void init(){
        auth = FirebaseAuth.getInstance();
        currentUser=auth.getCurrentUser();
    }

  protected void onStart() {
        if(currentUser == null){
            Intent welcomeIntent = new Intent(anaekran.this, MainActivity.class);
            startActivity(welcomeIntent);
            finish();
        }

        super.onStart();
    }

//YUKARIDAKİ KOD PARÇACIKALRI ANAEKRAN.JAVA CLASS IMIZDA BULUNAN VERİTABANI İLE İLGİLİ KOD PARÇACIKLARIDIR.
//BAŞARILI BİR EŞKİLDE GİRİŞ YAPILAN KULLANICININ ÇIKIŞINI OTOMATİK YAPILMAKTAN KAÇINILMIŞTIR.
//YANİ KULLANICI UYGULAMAYI HER AÇTIĞINDA GİRİŞ YAPMASI GEREKMEDİĞİNİ BELİRTİLMİŞTİR.
************************************************************************************************************************************************************************

DAHA PROGRAMIMIZ TASARIM AŞAMASINDA OLDUĞUNDAN DOLAYI BİRÇOK EKSİKLERİMİZ OLABİLİR.GEREKLİ DÜŞÜNDÜĞÜNÜZ KISIMLARI GİTHUB ÜZERİNDEN BAKARAK DÜZELTEBİLİRSİNİZ. 
GİTHUB LİNKİMİZ:
https://github.com/KisiselSaglikIzleme/Kisisel_Saglik_Izleme












































































