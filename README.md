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
import random
import math

# --- Configuração da Tela ---
wn = turtle.Screen()
wn.title("Pac-Turtle (Versão Simplificada)")
wn.bgcolor("black")
wn.setup(width=600, height=600)
wn.tracer(0)

# --- Variáveis do Jogo ---
score = 0
running = True

# --- Borda do Jogo ---
border_pen = turtle.Turtle()
border_pen.speed(0)
border_pen.color("blue")
border_pen.penup()
border_pen.setposition(-250, -250)
border_pen.pendown()
border_pen.pensize(3)
for _ in range(4):
    border_pen.forward(500)
    border_pen.left(90)
border_pen.hideturtle()

# --- Jogador (Pac-Man) ---
player = turtle.Turtle()
player.speed(0)
player.shape("circle")
player.color("yellow")
player.penup()
player.goto(0, -220)
player.direction = "stop"
player.speed = 2

# --- Fantasmas ---
ghosts = []
colors = ["red", "pink", "cyan", "orange"]
for color in colors:
    ghost = turtle.Turtle()
    ghost.speed(0)
    ghost.shape("triangle")
    ghost.color(color)
    ghost.penup()
    x = random.randint(-230, 230)
    y = random.randint(-100, 230)
    ghost.goto(x, y)
    ghost.dx = random.choice([-1, 1]) * 0.5
    ghost.dy = random.choice([-1, 1]) * 0.5
    ghosts.append(ghost)

# --- Comida (Pac-Dots) ---
foods = []
for _ in range(40):
    food = turtle.Turtle()
    food.speed(0)
    food.shape("circle")
    food.color("white")
    food.shapesize(0.5, 0.5)
    food.penup()
    x = random.randint(-230, 230)
    y = random.randint(-230, 230)
    food.goto(x, y)
    foods.append(food)

# --- Caneta de Pontuação ---
pen = turtle.Turtle()
pen.speed(0)
pen.color("white")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Pontuação: 0", align="center", font=("Courier", 24, "normal"))

# --- Funções de Movimento ---
def go_up():
    player.direction = "up"
def go_down():
    player.direction = "down"
def go_left():
    player.direction = "left"
def go_right():
    player.direction = "right"

def move_player():
    if player.direction == "up":
        y = player.ycor()
        player.sety(y + player.speed)
    if player.direction == "down":
        y = player.ycor()
        player.sety(y - player.speed)
    if player.direction == "left":
        x = player.xcor()
        player.setx(x - player.speed)
    if player.direction == "right":
        x = player.xcor()
        player.setx(x + player.speed)

    # Impedir que saia da borda
    if player.xcor() > 240: player.setx(240)
    if player.xcor() < -240: player.setx(-240)
    if player.ycor() > 240: player.sety(240)
    if player.ycor() < -240: player.sety(-240)

def move_ghosts():
    for ghost in ghosts:
        ghost.setx(ghost.xcor() + ghost.dx)
        ghost.sety(ghost.ycor() + ghost.dy)

        # Fazer fantasma quicar na borda
        if ghost.xcor() > 240 or ghost.xcor() < -240:
            ghost.dx *= -1
        if ghost.ycor() > 240 or ghost.ycor() < -240:
            ghost.dy *= -1

def check_collision(t1, t2):
    distance = math.sqrt(math.pow(t1.xcor() - t2.xcor(), 2) + math.pow(t1.ycor() - t2.ycor(), 2))
    return distance < 20

# --- Comandos do Teclado ---
wn.listen()
wn.onkeypress(go_up, "Up")
wn.onkeypress(go_down, "Down")
wn.onkeypress(go_left, "Left")
wn.onkeypress(go_right, "Right")
wn.onkeypress(go_up, "w")
wn.onkeypress(go_down, "s")
wn.onkeypress(go_left, "a")
wn.onkeypress(go_right, "d")

# --- Loop Principal do Jogo ---
while running:
    wn.update()
    
    move_player()
    move_ghosts()

    # Checar colisões
    for food in foods:
        if check_collision(player, food):
            food.goto(1000, 1000) # Mover para fora da tela
            foods.remove(food)
            score += 10
            pen.clear()
            pen.write(f"Pontuação: {score}", align="center", font=("Courier", 24, "normal"))

    for ghost in ghosts:
        if check_collision(player, ghost):
            pen.goto(0, 0)
            pen.write("FIM DE JOGO", align="center", font=("Courier", 36, "bold"))
            running = False

    # Checar condição de vitória
    if not foods:
        pen.goto(0, 0)
        pen.write("VOCÊ VENCEU!", align="center", font=("Courier", 36, "bold"))
        running = False

wn.mainloop()
