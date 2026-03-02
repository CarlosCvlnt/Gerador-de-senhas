import secrets
import string

def gerar_senha(length=12):
    if length < 4:
        raise ValueError("Senha tem que ser de pelo menos 4 caracteres.")

    minusculas = string.ascii_lowercase
    maiusculas = string.ascii_uppercase
    digitos = string.digits
    simbolos = string.punctuation

    senha = [
        secrets.choice(minusculas),
        secrets.choice(maiusculas),
        secrets.choice(digitos),
        secrets.choice(simbolos)
    ]

    digitosdasenha = minusculas + maiusculas + digitos + simbolos
    senha += [secrets.choice(digitosdasenha) for _ in range(length - 4)]

    secrets.SystemRandom().shuffle(senha)

    return ''.join(senha)

print("A senha gerada é:", gerar_senha(16))
