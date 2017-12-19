# EncryptLib


�ַ�����byte[]���ļ��ȶ���ļ��ܺͽ��ܹ��߼��ϣ������˶��ּ��ܷ�����

��������	ժҪ	��ط���
�򵥼���	��һ�ֱ����ʽ	Base64Util
�������	ֻ�ܼ��ܣ����ܽ���	MD5Util��SHAUtil
�ԳƼ���	ʹ����ͬ����Կ���ܺͽ���	AESUtil��DESUtil
�ǶԳƼ���	�ֹ�Կ��˽Կ��һ�����ܣ���һ������	RSAUtil
ʹ�÷���
Base64util
����	ժҪ
String base64EncodeStr(String str)	����
String base64DecodedStr(String str)	����
��Ԫ���ԣ�

System.out.println("base64");
// base64 �ַ������ܽ��ܲ���
assertEquals("R2NzU2xvb3DkuK3mloc=\n", Base64Util.base64EncodeStr("GcsSloop����"));
assertEquals("GcsSloop����", Base64Util.base64DecodedStr("R2NzU2xvb3DkuK3mloc=\n"));
MD5Util
����	ժҪ
String md5(String string)	�����ַ���
String md5(String string, String slat)	�����ַ���ͬʱ����
String md5(String string, int times)	��μ���
String md5(File file)	�����ļ���md5��ֵ
��Ԫ���ԣ�

System.out.println("md5");
// MD5 �ַ������ܲ���
assertEquals("", MD5Util.md5(""));
assertEquals("386d3ff3fa6def1ec307428e885e03a1", MD5Util.md5("GcsSloop����"));
assertEquals("fd01aa74bb73bbdb094bae28a558c6d1", MD5Util.md5("GcsSloop����", "salt"));

// MD5 ��μ��ܲ���
assertEquals("GcsSloop����", MD5Util.md5("GcsSloop����", 0));
assertEquals("386d3ff3fa6def1ec307428e885e03a1", MD5Util.md5("GcsSloop����", 1));
assertEquals("2d9fdd834c5c852fa2f946b670f3731f", MD5Util.md5("GcsSloop����", 2));
assertEquals("211dd7a16d5a01df756278cea9a38d53", MD5Util.md5("GcsSloop����", 3));

// MD5 �ļ�md5����
File file = new File("./Encrypt/Test/demo" +
                             ".flv");
assertEquals("a4e592e6160e0102e7ecc4ab6117b700", MD5Util.md5(file));
SHAUtil
����	ժҪ
String sha(String string, String type)	����
��Ԫ���ԣ�

System.out.println("sha");
// des �ַ������ܽ��ܲ���
String source = "GcsSloop����";
assertEquals("b9dd1d754ee3ac16dc584b8fd4655ca581a0637eab8ff25128b0a522372e7233",
             SHAUtil.sha(source, null));
assertEquals("34d44835ce4cc4d7ecf66428e49273bf02f748d7213be24c767c5f4f",
             SHAUtil.sha(source, SHAUtil.SHA224));
assertEquals("b9dd1d754ee3ac16dc584b8fd4655ca581a0637eab8ff25128b0a522372e7233",
             SHAUtil.sha(source, SHAUtil.SHA256));
assertEquals("2e3c27201c21b06b01289ebef09c9c36e752ca6a5b6425ca7b2501b4baaed29876954ca710b7e75c80b7b542df28fde6",
             SHAUtil.sha(source, SHAUtil.SHA384));
assertEquals("bc3f55fcb03272ee166d7804ccba348ffba05ddce08bf3fab719fa2c97c8dc71993fc9524e21b8fee9491aafc0b309ebca797163bca45ece7c3dd73dae3698ee",
             SHAUtil.sha(source, SHAUtil.SHA512));
AESUtil
����	ժҪ
String aes(String content, String password, int type)	���ܣ�����
��Ԫ���ԣ�

System.out.println("aes");
// aes �ַ������ܽ��ܲ���
String source = "GcsSloop����";
String key = "1234567890123456";
System.out.println("ԭ���� = " + source);
String aesStr = AESUtil.aes(source, key, Cipher.ENCRYPT_MODE);
System.out.println("���ܺ� = " + aesStr);
String result = AESUtil.aes(aesStr, key, Cipher.DECRYPT_MODE);
System.out.println("���ܺ� = " + result);
assertEquals(source, result);
DESUtil
����	ժҪ
String des(String content, String password, int type)	���ܣ�����
��Ԫ���ԣ�

System.out.println("des");
// des �ַ������ܽ��ܲ���
String source = "GcsSloop����";
String key = "1234567890123456";
System.out.println("ԭ���� = " + source);
String aesStr = DESUtil.des(source, key, Cipher.ENCRYPT_MODE);
System.out.println("���ܺ� = " + aesStr);
String result = DESUtil.des(aesStr, key, Cipher.DECRYPT_MODE);
System.out.println("���ܺ� = " + result);
assertEquals(source, result);
RSAUtil
����	ժҪ
Map<String, Object> getKeyPair()	�����ȡ��Կ(��Կ��˽Կ), �ͻ��˹�Կ���ܣ�������˽Կ����
String getKey(Map<String, Object> keyMap, boolean isPublicKey)	��ȡ��Կ/˽Կ(true����ȡ��Կ��false����ȡ˽Կ)
String sign(byte[] data, String privateKey)	��ȡ����ǩ��
boolean verify(byte[] data, String publicKey, String sign)	����ǩ��У��
byte[] rsa(byte[] data, String string, int type)	Rsa����/���ܣ�һ������£���Կ����˽Կ���ܣ�
��Ԫ���ԣ�

System.out.println("rsa");
// des �ַ������ܽ��ܲ���
byte[] data = "GcsSloop����".getBytes();

// ��Կ������ǩ����ȡ
Map<String, Object> keyMap = RSAUtil.getKeyPair();
String publicKey = RSAUtil.getKey(keyMap, true);
System.out.println("rsa��ȡ��Կ�� " + publicKey);
String privateKey = RSAUtil.getKey(keyMap, false);
System.out.println("rsa��ȡ˽Կ�� " + privateKey);

// ��Կ����˽Կ����
byte[] rsaPublic =
        RSAUtil.rsa(data, publicKey, RSAUtil.RSA_PUBLIC_ENCRYPT);
System.out.println("rsa��Կ���ܣ� " + new String(rsaPublic));
System.out.println("rsa˽Կ���ܣ� " + new String(
        RSAUtil.rsa(rsaPublic, privateKey, RSAUtil.RSA_PRIVATE_DECRYPT)));

// ˽Կ���ܹ�Կ����
byte[] rsaPrivate =
        RSAUtil.rsa(data, privateKey, RSAUtil.RSA_PRIVATE_ENCRYPT);
System.out.println("rsa˽Կ���ܣ� " + new String(rsaPrivate));
System.out.println("rsa��Կ���ܣ� " + new String(
        RSAUtil.rsa(rsaPrivate, publicKey, RSAUtil.RSA_PUBLIC_DECRYPT)));

// ˽Կǩ������Կǩ��У��
String signStr = RSAUtil.sign(rsaPrivate, privateKey);
System.out.println("rsa����ǩ�����ɣ� " + signStr);
System.out.println("rsa����ǩ��У�飺 " + RSAUtil.verify(rsaPrivate, publicKey, signStr));