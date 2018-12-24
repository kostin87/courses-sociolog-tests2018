---
title: 'Test 1'
description: 'Тестирование по эконометрии'
attachments: null
---

## Создание векторов 1

```yaml
type: NormalExercise
key: 98360b49d2
lang: r
xp: 100
skills: 5
```



`@instructions`
- У вас есть вектор x
- Создайте вектор y  (1,2,3....) той же длинны что и вектор x.

`@hint`
Воспользуйтесь оператором ":"

`@pre_exercise_code`
```{r}
x=rnorm(round(runif(1,100,1000),0))
```

`@sample_code`
```{r}
y=

```

`@solution`
```{r}
y=1:NROW(x)
```

`@sct`
```{r}
ex() %>% check_object("y") %>% check_equal()
success_msg("Отлично!")
```

---

## Создание векторов 2

```yaml
type: NormalExercise
key: 61f0a215c8
lang: r
xp: 100
skills: 5
```



`@instructions`
- Сгенирируйте случайный вектор z длинной x, состоящий из случайных величин распределенных нормально с мат. ожиданием 10 и стандартным отклонением 100.

`@hint`
Используйте функцию rnorm

`@pre_exercise_code`
```{r}
x=round(runif(1,100,1000))
```

`@sample_code`
```{r}
z=

```

`@solution`
```{r}
z=rnorm(x,10,100)
```

`@sct`
```{r}
ex() %>% check_object("z") %>% check_equal()
success_msg("Отлично!")
```

---

## Отрисовка гистограмм

```yaml
type: NormalExercise
key: 15e90a572d
lang: r
xp: 100
skills: 5
```



`@instructions`
- У вас есть случайная величина x.
- Постройте её гистограмму с разбиением на 100 столбцов.

`@hint`


`@pre_exercise_code`
```{r}
x=rchisq(10000, 40)
```

`@sample_code`
```{r}
x

```

`@solution`
```{r}
hist(x,breaks = 100)
```

`@sct`
```{r}
ex() %>% check_function("hist") %>% {
  check_arg(., "x") %>% check_equal()
  check_arg(., "breaks") %>% check_equal()
}
success_msg("Отлично!")
```

---

## Определение распределения

```yaml
type: MultipleChoiceExercise
key: c360e6347f
xp: 50
```

У нас есть случайная величина x. Как вы думаете к какому распределению она относится?

`@possible_answers`
- 'Нормальное'
- 'Хи-квадрат'
- 'Стьюдента'

`@hint`
Нарисуйте гистограмму

`@pre_exercise_code`
```{r}
x=rchisq(10000, 40)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
ex() %>% check_mc(2, feedback_msgs = c(msg2, msg3))
```

---

## Таблица сопряженности 1

```yaml
type: NormalExercise
key: 44d031f162
lang: r
xp: 100
skills: 5
```



`@instructions`
- У вас есть две фиктивные переменные x и y.
- Постройте таблицу z сопряженности этих переменных.

`@hint`
Используйте функцию table.

`@pre_exercise_code`
```{r}
x=round(round(runif(10000)))
y=round(round(runif(10000)))
```

`@sample_code`
```{r}
z=

```

`@solution`
```{r}
z=table(x,y)
```

`@sct`
```{r}
ex() %>% check_object("z") %>% check_equal()
success_msg("Отлично!")
```

---

## Таблица сопряженности 2

```yaml
type: MultipleChoiceExercise
key: 7726022a2b
xp: 50
```

- У вас есть таблица сопряженности z
- Существует ли зависимость между переменными в случае если вы выбрали 5% квантиль.

`@possible_answers`
- Зависимость существует
- Зависимости нет

`@hint`


`@pre_exercise_code`
```{r}
x=round(round(runif(10000)))
y=round(round(runif(10000)))
z=table(x,y)
z[1,1]=z[1,1]+200
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=chisq.test(z)
if(a$p.value>0.05){
  r=2
}else{r=1}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Фиктивные переменные. Создание

```yaml
type: NormalExercise
key: 8ed83c7cd0
lang: r
xp: 100
skills: 1
```



`@instructions`
- У вас есть вектор x.
- Создайте вектор y, который был бы TRUE если x больше 10 и FALSE иначе
- Создайте переменную z, которая показывала бы сколько значений y является FALSE

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(round(runif(1,100,1000),0),8,10)
```

`@sample_code`
```{r}
y=
z=
```

`@solution`
```{r}
y=x>10
z=sum(abs(y-1))

```

`@sct`
```{r}
ex() %>% check_object("y")  %>% check_equal()
ex() %>% check_object("z")  %>% check_equal()
success_msg("Отлично!")
```

---

## Фиктивные переменные. Анализ

```yaml
type: NormalExercise
key: c5c9f67f18
lang: r
xp: 100
skills: 1
```



`@instructions`
- У вас есть вектор x и y.
- Создайте переменную z, которая показывала бы сколько значений x больше y минус сколько значений y больше x

`@hint`
Используйте функцию sum

`@pre_exercise_code`
```{r}
x=rnorm(round(runif(1,100,1000),0),8,10)
y=rnorm(NROW(x),6,5)
```

`@sample_code`
```{r}
z=
```

`@solution`
```{r}
z=sum(x>y)-sum(y>x)
```

`@sct`
```{r}
ex() %>% check_object("z") %>% check_equal()
success_msg("Отлично!")
```

---

## Объединение векторов

```yaml
type: NormalExercise
key: cfdb284084
lang: r
xp: 100
skills: 5
```



`@instructions`
- У вас есть два вектора c1 и c2, объедините их в матрицу с двумя строками c3.

`@hint`
Именно строками

`@pre_exercise_code`
```{r}
c1=rnorm(1000)
c2=rnorm(1000)

```

`@sample_code`
```{r}
c3=

```

`@solution`
```{r}
c3=rbind(c1,c2)
```

`@sct`
```{r}
ex() %>% check_object("c3") %>% check_equal()
success_msg("Отлично!")
```

---

## Линейная регрессия

```yaml
type: NormalExercise
key: 6ca86c7e87
lang: r
xp: 100
skills: 5
```



`@instructions`
- Постройте линейную регрессию x от y и z и запишите ее в переменную fit.

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,1.5)
z=x>2
```

`@sample_code`
```{r}
fit=

```

`@solution`
```{r}
fit=lm(x~y+z)
```

`@sct`
```{r}
ex() %>% check_object("fit") %>% check_equal()
success_msg("Отлично!")
```

---

## Результаты регрессии1

```yaml
type: MultipleChoiceExercise
key: dd5093e3d3
lang: r
xp: 50
skills: 1
```

У вас есть результаты линейной регрессии fit. Является ли регрессия значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=x+rnorm(10000,0,5)>3
fit=lm(x~y+z)

```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$fstatistic[1]>qf(0.95,a$fstatistic[2],a$fstatistic[3])){
  r=1
}else{r=2}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии2

```yaml
type: MultipleChoiceExercise
key: ba1aef6938
lang: r
xp: 50
skills: 1
```

У вас есть результаты линейной регрессии fit. Является ли переменная y значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=x+rnorm(10000,0,5)>3
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$coefficients[2,4]>0.05){
  r=2
}else{r=1}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии3

```yaml
type: MultipleChoiceExercise
key: d2043621d1
lang: r
xp: 50
skills: 1
```

У вас есть результаты линейной регрессии fit. Является ли переменная zTRUE значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=x+rnorm(10000,0,5)>3
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$coefficients[3,4]>0.05){
  r=2
}else{r=1}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии4

```yaml
type: MultipleChoiceExercise
key: f067ffdee0
xp: 50
```

У вас есть результаты линейной регрессии fit. Что обозначает переменная zTRUE?

`@possible_answers`
- В среднем x больше у на величину коэффициента zTRUE
- x является положительной величиной, потому что zTRUE>0
- На сколько в среднем x в случае z TRUE больше, чем x в случае z FALSE
- На сколько в среднем x в случае z TRUE больше, чем x в случае z FALSE, делить пополам

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=x+rnorm(10000,0,5)>3
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
ex() %>% check_mc(3, feedback_msgs = c(msg2, msg3))
```
