# PRIMEIRO_RESPOSITORY
Criei minha primeira pasta 
# Olá, mundo! 👋 Eu sou o André Santos Silva Júnior

![Python Logo](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)

---

## Sobre mim
- 👦 Idade: 16 anos  
- 🐍 Apaixonado por Python e programação  
- 🎯 Objetivo: Ingressar na área de desenvolvimento e crescer cada vez mais!  
- 📚 Atualmente estudando lógica de programação, estruturas de dados e projetos divertidos em Python.

---

## Joguinho para você brincar 🕹️

Aqui vai um joguinho simples que eu criei para você testar no seu terminal! É um jogo de adivinhação de números. Bora jogar?

```python
import random

def jogo_adivinhacao():
    print("🎉 Bem-vindo ao Jogo de Adivinhação do André! 🎉")
    numero_secreto = random.randint(1, 20)
    tentativas = 5

    while tentativas > 0:
        chute = int(input(f"Tente adivinhar o número entre 1 e 20 (Você tem {tentativas} tentativas): "))
        if chute == numero_secreto:
            print("🎉 Parabéns! Você acertou! 🎉")
            break
        elif chute < numero_secreto:
            print("Dica: Tente um número maior.")
        else:
            print("Dica: Tente um número menor.")
        tentativas -= 1

    if tentativas == 0:
        print(f"Fim de jogo! O número secreto era {numero_secreto}. Tente novamente!")

if __name__ == "__main__":
    jogo_adivinhacao()

from PIL import Image, ImageDraw, ImageFont
import os

# Texto para animar
frames_text = [
    "Keep Calm",
    "and Code",
    "Python!",
    "Errors? Bugs?",
    "Relax, it's part",
    "of the game 🐍🔥"
]

# Configurações do GIF
width, height = 400, 200
background_color = (30, 144, 255)  # Azul Python
text_color = (255, 255, 255)
font_path = "arial.ttf"  # Ou um caminho para uma fonte no seu PC
font_size = 30

frames = []

# Cria frames com textos diferentes
for text in frames_text:
    img = Image.new("RGB", (width, height), background_color)
    draw = ImageDraw.Draw(img)
    try:
        font = ImageFont.truetype(font_path, font_size)
    except:
        font = ImageFont.load_default()
    w, h = draw.textsize(text, font=font)
    draw.text(((width-w)/2, (height-h)/2), text, font=font, fill=text_color)
    frames.append(img)

# Salvar como GIF animado
frames[0].save('python_motivacional.gif', format='GIF',
               append_images=frames[1:], save_all=True, duration=1000, loop=0)

print("GIF criado: python_motivacional.gif")

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/seu-perfil)  
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/sants_andre0)  
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)  
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)  
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)  
[![VSCode](https://img.shields.io/badge/VSCode-0078D7?style=for-the-badge&logo=visual-studio-code&logoColor=white)](https://code.visualstudio.com/)  
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)  
[![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)  
[![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
