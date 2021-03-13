---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №5: Модель "Хищник-жертва"
subtitle: "*дисциплина: Математическое моделирование*"
author: "Швец С., НФИбд-03-18"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
#lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: luatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Введение

  Онсновная цель работы - изучить и построить модель хищник-жертва(модель Лотки-Вольтерры)

## Задачи работы

Выделим основные задачи работы:

- Изучить жесткую модель хищник-жертва
- Изучит модель хищник-жертва с малым изменением
- Построить жесткую модель хищник-жертва

# Терминология. Условные обозначения

Простейшая модель взаимодействия двух видов типа «хищник — жертва» - *модель Лотки-Вольтерры*. Данная модель основывается на следующих предположениях:

1. Численность популяции жертв $x$ и хищников $y$ зависят только от времени
2. В отсутствии взаимодействия численность видов изменяется по модели Мальтуса, при этом число жертв увеличивается, а число хищников падает
3. Естественная смертность жертвы и естественная рождаемость хищника несущественны
4. Эффект насыщения численности обеих популяций не учитывается
5. Скорость роста численности жертв уменьшается пропорционально численности хищников


**Математическа модель**


$$
\begin{cases}
\frac{dx}{dt} =  ax(t) - bx(t)y(t)
\\
\frac{dx}{dt} =  -cy(t) + dx(t)y(t)
\end{cases}
$$

- $x$ - число жертв
- $y$ - число хищников
- $a$ -  коэффициент, описывающий скорость естественного прироста числа жертв в отсутствие хищников
- $c$ - естественное вымирание хищников, лишенных пищи в виде жертв.

Вероятность взаимодействия жертвы и хищника пропорциональна как количеству жертв, так и числу самих хищников (xy). Каждый акт взаимодействия уменьшает популяцию жертв, но способствует увеличению популяции хищников.

Математический анализ жесткой модели показывает, что имеется стационарное состояние, всякое же другое начальное состояние(B) приводит к периодическому колебанию численности как жертв, так и хищников, так что по прошествии некоторого времени система возвращается в состояние B.



Стационарное состояние системы (положение равновесия, не зависящее от времени решение) будет в точке:

$$x_0 = \frac{c}{d}
\\
y_0 = \frac{a}{d}$$

Если начальные значения задать в стационарном состоянии $x(0) = x_0, y(0)=y_0$, то в любой момент времени численность популяций изменяться не будет.


При малом изменении модели:


$$
\begin{cases}
\frac{dx}{dt} =  ax(t) - bx(t)y(t) + \varepsilon f(x,y)
\\
\frac{dx}{dt} = -cy(t) + dx(t)y(t) + \varepsilon g(x,y), \varepsilon \ll 1
\end{cases}
$$

Прибавленые к правым частям малые члены, учитывают конкуренцию жертв за пищу и хищников за жертв и т.п.

Вывод о периодичности, справедливый для жесткой системы Лотки-Вольтерры, теряет силу. Таким образом, мы получаем так называемую мягкую модель «хищник-жертва».

В зависимости от вида малых поправок f и g возможны 3 случая:

1. Равновесное состояние A устойчиво. При любых других начальных условиях через большое время устанавливается именно оно.
2. Система стационарное состояние неустойчиво. Эволюция приводит то к резкому увеличению числа хищников, то к их почти полному вымиранию.
3. В системе с неустойчивым стационарным состоянием A с течением времени устанавливается периодический режим.


**Вывод:** жесткую модель всегда надлежит исследовать на структурную устойчивость полученных при ее изучении результатов по отношению к малым изменениям модели (делающим ее мягкой).



# Выполнение лабораторной работы

## Задача:

**Вариант 7**

Для модели «хищник-жертва»:

$$
\begin{cases}
\frac{dx}{dt} =  -0.18x(t) + 0.047x(t)y(t)
\\
\frac{dx}{dt} = 0.38y(t) - 0.035x(t)y(t)
\end{cases}
$$


Постройте график зависимости численности хищников от численности жертв, а также графики изменения численности хищников и численности жертв при следующих начальных условиях: $x_0 = 12, y_0 = 17$. Найдите стационарное состояние системы.



## Решение

**Коэффиценты:**


- a= 0.18 // коэффициент естественной смертности хищников
- b= 0.38; // коэффициент естественного прироста жертв
- c= 0.047; // коэффициент увеличения числа хищников
- d= 0.035; // коэффициент смертности жертв

*Код на Julia:*
```
using  Gadfly
using Plots
using DifferentialEquations

a= 0.18;
b= 0.38;
c= 0.047;
d= 0.035;
x0 = 12;
y0 =17;

    function syst(dy,y,p,t)
        dy[1] = -a*y[1]+c*y[1]*y[2]
        dy[2] = b*y[2]-d*y[1]*y[2]
    end

y_0 = [x0, y0];
tspan = (0, 300);


prob = ODEProblem(syst, y_0, tspan);
sol = solve(prob, RK4(),reltol=1e-6, timeseries_steps = 0.01);

N = length(sol.u)
    J = length(sol.u[1])
    U = zeros(N, J)

    for i in 1:N, j in 1:J
        U[i,j] = sol.u[i][j]
    end




set_default_plot_size(20cm, 15cm)
Gadfly.plot(x = U[:,1], y = U[:,2],
Theme(  discrete_highlight_color=x->"orange",
                default_color="orange",
                key_title_color="black",
                background_color="white",),)

Plots.plot(sol)



```

![График зависимости численности хищников от численности жертв](01.png){ #fig:001 width=70% }

![График изменения численности хищников(u1(t)) и численности жертв(u2(t))](02.png){ #fig:002 width=70% }



# Выводы

Мы изучили и построили модель хищник-жертва
