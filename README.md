# androidsystemcertificate
    1. Save your certificate in the PEM format
    2. Get the subject of the certificate with "openssl x509 -inform PEM -subject_hash -in CERTIFICATE.FILE" It should be in a format similar to eg "0b112a89"
    3. Save the certificate into a text file with "openssl x509 -inform PEM -text -in CERTIFICATE.FILE > yourcert.txt"
    4. Switch the PEM section and the text, "-----BEGIN CERTIFICATE-----[...]" has to be at the beginning of the file
    5. Rename the file to 0b112a89.0 (replace with the subject you got in step 2)
    6. Copy the file into /system/etc/security/cacerts/ and make sure chmod permissions are set to 0644 (rw,r,r)
    7. Your certificate should now show up in the trusted certificate list
    8. If that doesn't work, disable and enable the certificate in Android Settings, which creates a file in /data/misc/keychain/cacerts-added/. Move that file to /system/etc/security/cacerts/ and delete your original file from step 6
