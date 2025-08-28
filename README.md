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


    if head.xcor() > 290 or head.xcor() < -290 or head.ycor() > 290 or head.ycor() < -290:
        time.sleep(1)
        head.goto(0, 0)
        head.direction = "stop"
        for segment in segments:
            segment.goto(1000, 1000)
        segments.clear()
        score = 0
        delay = 0.1
        pen.clear()
        pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))

    if head.distance(food) < 20:
        x = random.randint(-280, 280)
        y = random.randint(-280, 280)
        food.goto(x, y)

        new_segment = turtle.Turtle()
        new_segment.speed(0)
        new_segment.shape("square")
        new_segment.color("lightgreen")
        new_segment.penup()
        segments.append(new_segment)

        delay -= 0.001
        score += 10

        if score > high_score:
            high_score = score
        
        pen.clear()
        pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))

    for index in range(len(segments) - 1, 0, -1):
        x = segments[index - 1].xcor()
        y = segments[index - 1].ycor()
        segments[index].goto(x, y)

    if len(segments) > 0:
        x = head.xcor()
        y = head.ycor()
        segments[0].goto(x, y)

    move()

    for segment in segments:
        if segment.distance(head) < 20:
            time.sleep(1)
            head.goto(0, 0)
            head.direction = "stop"
            for seg in segments:
                seg.goto(1000, 1000)
            segments.clear()
            score = 0
            delay = 0.1
            pen.clear()
            pen.write("Pontuação: {}  Recorde: {}".format(score, high_score), align="center", font=("Courier", 24, "normal"))

    time.sleep(delay)

wn.mainloop()
