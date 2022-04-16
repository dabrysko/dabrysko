from tkinter import *
root=Tk()

c = Canvas(root, width=400, height=400, bg='white')
c.pack()

x0=0
y0=0

def PPP(event):
    global x0
    global y0
    x0 = event.x
    y0 = event.y
    motion()
def motion():
    x=c.coords(ball)[0]
    y=c.coords(ball)[1]
    dx=x0-x
    dy=y0-y
    c.move(ball, dx/5, dy/5)
    if c.coords(ball)[1] <200 and c.coords(ball)[2] <300 :
        root.after(1000,motion)

ball=c.create_oval(0, 100, 40, 140, fill='green')
c.bind('<Button-1>', PPP)

motion()


root.mainloop()
