-> STRİNG BİRLEŞTİRME 

//BEFORE
OBJECT:
STRING AD, 
STRING SOYAD,
STRING ADSOYAD;

//AFTER
SET GROUPSONUC TO HIDE;

//BİRLEŞTİR BUTONU
AD = SCAD;
SOYAD  = SCSOYAD;
ADSOYAD = AD + ' ' + SOYAD;
FULLTEXT = ADSOYAD;
SET GROUPSONUC TO SHOW;



--> HESAP MAKİNESİ 

//BEFORE 
OBJECT:
INTEGER S1,
INTEGER S2,
INTEGER S3,
STRING ISLEM;


//OK BUTONU
S1=SCSAYI1;
S2=SCSAYI2;
ISLEM=SCISLEM;

IF ISLEM == '+' THEN
	S3=S1+S2;
	SCTOTAL=S3;
ELSE
	IF ISLEM == '-' THEN
		S3=S1-S2;
		SCTOTAL=S3;
	ELSE
		IF ISLEM == '*' THEN
			S3=S1*S2;
			SCTOTAL=S3;
		ELSE
			IF ISLEM == '/' THEN
				S3=S1/S2;
				SCTOTAL=S3;
			ELSE
				MESSAGE BAS W2000 WITH 'Gecersiz islem';
			ENDIF;
		ENDIF;
	ENDIF;
ENDIF;




--> HESAP MAKİNESİ -CLASS METOD

//BEFORE
OBJECT:
STRING ISLEM,
EDUT1911CLASS2 EDUT1911CLASS2REC;


//OK BUTONU 
ISLEM  = SCISLEM;
SWITCH ISLEM
CASE '+':
    SONUC  = EDUT1911CLASS2REC.TOPLA(SCSAYI1 , SCSAYI2);
CASE '-':
    SONUC = EDUT1911CLASS2REC.CIKAR(SCSAYI1 , SCSAYI2);
CASE '*':
    SONUC = EDUT1911CLASS2REC.CARP(SCSAYI1 , SCSAYI2);
CASE '/':
    SONUC = EDUT1911CLASS2REC.BOL(SCSAYI1 , SCSAYI2);
DEFAULT:
    MESSAGE BAS W2000 WITH 'GECERSİZ İSLEM GİRİLDİ.';
ENDSWITCH;



CLASS
//TÜM SININF İÇİNDE KULLANACAGIMIZ GLOBAL DEĞİKENİMİZİ BURADA TANIMLIYORUZ
OBJECT:
INTEGER S3;

//METODLAR

//TOPLA 
//DEĞİKENLERİMİZİ PARAMETERS İÇİNDE TANIMLIYORUZ
PARAMETERS:
INTEGER S1,
INTEGER S2;
S3 = S1 + S2;
RETURN S3;

//CIKAR 
PARAMETERS:
INTEGER S1,
INTEGER S2;
S3 = S1 - S2;
RETURN S3;

//BOL 
PARAMETERS:
INTEGER S1,
INTEGER S2;
S3 = S1 / S2;
RETURN S3;

//CARP 
PARAMETERS:
INTEGER S1,
INTEGER S2;
S3 = S1 * S2;
RETURN S3;






