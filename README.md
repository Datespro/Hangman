import random

def hangman():
    palabras = ["python", "elefante", "computadora", "jardin", "programa", "robot"]
    palabra = random.choice(palabras)
    progreso = ["_"] * len(palabra)
    intentos = 6
    letras_usadas = set()

    print("🎮 ¡Bienvenido al juego de Hangman!")

    while intentos > 0 and "_" in progreso:
        print("\nPalabra:", " ".join(progreso))
        print("Intentos restantes:", intentos)
        print("Letras usadas:", ", ".join(sorted(letras_usadas)))

        letra = input("Elige una letra: ").lower()

        if len(letra) != 1 or not letra.isalpha():
            print("Por favor escribe solo una letra.")
            continue

        if letra in letras_usadas:
            print("Ya intentaste esa letra.")
            continue

        letras_usadas.add(letra)

        if letra in palabra:
            print("✔️ ¡Correcto!")
            for i, l in enumerate(palabra):
                if l == letra:
                    progreso[i] = letra
        else:
            print("❌ Incorrecto.")
            intentos -= 1

    if "_" not in progreso:
        print("\n🎉 ¡Ganaste! La palabra era:", palabra)
    else:
        print("\n💀 Perdiste. La palabra era:", palabra)

hangman()
