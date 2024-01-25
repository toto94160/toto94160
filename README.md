
import base64
from cryptography.fernet import Fernet

# Clé secrète utilisée pour le chiffrement (à des fins démonstratives uniquement)
secret_key = b'w8FjwYZJ-XdMbsvp1Oi7z9RfiTZukn5VvlTz5CpP07A='
cipher = Fernet(secret_key)

# Contenu chiffré du fichier flag.notes (à des fins démonstratives uniquement)
encrypted_content = b'gAAAAABfYLuhkI3Hj1kl0ZQq7Tk8mIakV-mi8du7h1aQJzjnfM1iO13d8WbbdMoAZ6Ft-0yyQR06nNpv4LbG1EPkVJvJYhVzsw=='

def decrypt_content(encrypted_content, cipher):
    decrypted_content = cipher.decrypt(encrypted_content)
    return decrypted_content.decode('utf-8')

try:
    decrypted_flag = decrypt_content(base64.urlsafe_b64decode(encrypted_content), cipher)
    print(f'Flag déchiffré: {decrypted_flag}')
except Exception as e:
    print(f'Erreur lors du déchiffrement : {str(e)}')
