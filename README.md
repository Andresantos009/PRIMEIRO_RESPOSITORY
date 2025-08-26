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
import curses
import random

def jogo_cobrinha():
    # Inicializa a tela
    tela = curses.initscr()
    curses.curs_set(0)  # Oculta o cursor
    altura, largura = tela.getmaxyx()
    janela = curses.newwin(altura, largura, 0, 0)
    janela.keypad(True)  # Habilita captura de teclas especiais (setas)
    janela.timeout(100)  # Tempo de atualização da tela em ms

    # Posição inicial da cobrinha (3 blocos)
    cobrinha_x = largura // 4
    cobrinha_y = altura // 2
    cobrinha = [
        [cobrinha_y, cobrinha_x],
        [cobrinha_y, cobrinha_x - 1],
        [cobrinha_y, cobrinha_x - 2]
    ]

    # Primeira comida
    comida = [random.randint(1, altura - 2), random.randint(1, largura - 2)]
    janela.addch(comida[0], comida[1], curses.ACS_PI)

    key = curses.KEY_RIGHT  # Direção inicial
    score = 0

    while True:
        prox_tecla = janela.getch()
        key = key if prox_tecla == -1 else prox_tecla

        # Calcula nova posição da cabeça da cobrinha
        nova_cabeca = [cobrinha[0][0], cobrinha[0][1]]

        if key == curses.KEY_DOWN:
            nova_cabeca[0] += 1
        elif key == curses.KEY_UP:
            nova_cabeca[0] -= 1
        elif key == curses.KEY_LEFT:
            nova_cabeca[1] -= 1
        elif key == curses.KEY_RIGHT:
            nova_cabeca[1] += 1

        # Insere a nova cabeça na lista da cobrinha
        cobrinha.insert(0, nova_cabeca)

        # Se a cobrinha comeu a comida
        if cobrinha[0] == comida:
            score += 1
            comida = None
            # Gera nova comida em posição aleatória que não esteja na cobrinha
            while comida is None:
                nova_comida = [
                    random.randint(1, altura - 2),
                    random.randint(1, largura - 2)
                ]
                if nova_comida not in cobrinha:
                    comida = nova_comida
            janela.addch(comida[0], comida[1], curses.ACS_PI)
        else:
            # Remove a cauda da cobrinha
            cauda = cobrinha.pop()
            janela.addch(cauda[0], cauda[1], ' ')

        # Verifica colisão com paredes ou com o próprio corpo
        if (cobrinha[0][0] in [0, altura] or
            cobrinha[0][1] in [0, largura] or
            cobrinha[0] in cobrinha[1:]):
            curses.endwin()
            print(f"Game Over! Sua pontuação foi: {score}")
            break

        # Desenha a cobrinha na tela
        janela.addch(cobrinha[0][0], cobrinha[0][1], curses.ACS_CKBOARD)

if __name__ == "__main__":
    print("Joguinho da cobrinha iniciado! Use as setas para jogar.")
    print("Pressione Ctrl+C para sair.")
    jogo_cobrinha()


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
