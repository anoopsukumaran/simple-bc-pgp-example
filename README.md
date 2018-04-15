# simple-bc-pgp-example
I have written a simple pgp utility using Bouncy Castle dependency that would help you to Encrypt-Decrypt a file using a public & a private key.

Note : The utility jar's are been placed under target folder.

How to run the utility ?

1. To generate Public & Private Key use the below command.

java -jar pgpKeyGen.jar -a identity sample

*sample is a key phrase [ you can use anything ] that would be needed later to decrypt the file.

2. To encrypt a file use the below command where pub.asc is the public key that we generated.
 
java -jar pgpEncryptDecryptModule.jar -e filename.txt pub.asc

3. To decrypt a file use the below command where secret.asc is the secret key that was generated & "sample" is the key phrase which we used during keygen creation.

java -jar pgpEncryptDecryptModule.jar -d filename.txt.bpg secret.asc sample

---------------------------------------------------------------------------

I had to make few JAVA configuration changes to make it work ! 

1. GoTo C:\Program Files\Java\jdk1.7.0_79\jre\lib\security\

This was done to remove the security restriction on the Key Length.

Replace local_policy.jar & US_export_policy.jar from

http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html

2. GoTo C:\Program Files\Java\jdk1.7.0_79\jre\lib\security\java.security 

Make a new entry as below under - List of providers and their preference orders.

security.provider.11=org.bouncycastle.jce.provider.BouncyCastleProvider

3. Place BouncyCastle jar's under C:\Program Files\Java\jdk1.7.0_79\jre\lib\ext

bcpg-jdk15on-1.59.jar
bcprov-jdk15on-1.59.jar
