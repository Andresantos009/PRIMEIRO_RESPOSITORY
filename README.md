# PRIMEIRO_RESPOSITORY
Criei minha primeira pasta 
# Olá, mundo! 👋 Eu sou o André Santo

![Python Logo](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)

---

## Sobre mim
- 👦 Idade: 16 anos  
- 🐍 Apaixonado por Python e programação  
- 🎯 Objetivo: Ingressar na área de desenvolvimento e crescer cada vez mais!  
- 📚 Atualmente estudando lógica de programação, estruturas de dados e projetos divertidos em Python.



[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/sants_andre0)  

import turtle
import time
import random

delay = 0.1

# Pontuação
score = 0
high_score = 0

# Configuração da tela
wn = turtle.Screen()
wn.title("Jogo da Cobrinha")
wn.bgcolor("black")
wn.setup(width=600, height=600)
wn.tracer(0)  # Desliga as atualizações automáticas da tela

# Cabeça da cobra
head = turtle.Turtle()
head.speed(0)
head.shape("square")
head.color("green")
head.penup()
head.goto(0, 0)
head.direction = "stop"

# Comida da cobra
food = turtle.Turtle()
food.speed(0)
food.shape("circle")
food.color("red")
food.penup()
food.goto(0, 100)

segments = []

# Caneta para escrever a pontuação
pen = turtle.Turtle()
pen.speed(0)
pen.shape("square")
pen.color("white")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Pontuação: 0  Recorde: 0", align="center", font=("Courier", 24, "normal"))

# Funções
def go_up():
    if head.direction != "down":
        head.direction = "up"

def go_down():
    if head.direction != "up":
        head.direction = "down"

def go_left():
    if head.direction != "right":
        head.direction = "left"

def go_right():
    if head.direction != "left":
        head.direction = "right"

def move():
    if head.direction == "up":
        y = head.ycor()
        head.sety(y + 20)

    if head.direction == "down":
        y = head.ycor()
        head.sety(y - 20)

    if head.direction == "left":
        x = head.xcor()
        head.setx(x - 20)

    if head.direction == "right":
        x = head.xcor()
        head.setx(x + 20)

# Comandos do teclado
wn.listen()
wn.onkeypress(go_up, "Up")
wn.onkeypress(go_down, "Down")
wn.onkeypress(go_left, "Left")
wn.onkeypress(go_right, "Right")
wn.onkeypress(go_up, "w")
wn.onkeypress(go_down, "s")
wn.onkeypress(go_left, "a")
wn.onkeypress(go_right, "d")

# Loop principal do jogo
while True:
    wn.update()

    # Checar colisão com a borda
    if head.xcor() > 290 or head.xcor() < -290 or head.ycor() > 290 or head.ycor() < -290:
        time.sleep(1)
        head.goto(0, 0)
        head.direction = "stop"

        # Esconder os segmentos
        for segment in segments:
            segment.goto(1000, 1000)
        
        segments.clear()
        score = 0
        delay = 0.1
        pen.clear()
        pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))


    # Checar colisão com a comida
    if head.distance(food) < 20:
        # Mover a comida para um lugar aleatório
        x = random.randint(-280, 280)
        y = random.randint(-280, 280)
        food.goto(x, y)

        # Adicionar um segmento
        new_segment = turtle.Turtle()
        new_segment.speed(0)
        new_segment.shape("square")
        new_segment.color("lightgreen")
        new_segment.penup()
        segments.append(new_segment)

        # Aumentar a velocidade
        delay -= 0.001

        # Aumentar a pontuação
        score += 10

        if score > high_score:
            high_score = score
        
        pen.clear()
        pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))

    # Mover os segmentos do corpo em ordem reversa
    for index in range(len(segments) - 1, 0, -1):
        x = segments[index - 1].xcor()
        y = segments[index - 1].ycor()
        segments[index].goto(x, y)

    # Mover o segmento 0 para onde a cabeça estava
    if len(segments) > 0:
        x = head.xcor()
        y = head.ycor()
        segments[0].goto(x, y)

    move()

    # Checar colisão com o próprio corpo
    for segment in segments:
        if segment.distance(head) < 20:
            time.sleep(1)
            head.goto(0, 0)
            head.direction = "stop"

            # Esconder os segmentos
            for seg in segments:
                seg.goto(1000, 1000)

            segments.clear()
            score = 0
            delay = 0.1
            pen.clear()
            pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))

    time.sleep(delay)

wn.mainloop()
