import sqlite3
from tkinter import *
from tkinter import messagebox
import tkinter as tk
from tkinter import ttk
from datetime import datetime
import matplotlib.pyplot as plt
import pandas as pd
con=sqlite3.connect('users.db')
cur=con.cursor()
df=pd.read_csv("Book11.csv")
print(df['13-10-2023'])
a=tk.Tk()
b="white"
Id=0
#flat, raised, sunken, groove, ridge, solid)
label1 = tk.Label(a, 
                 text="""                                                    


























                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                """, 
                 bd=1,              # Set border width (change to desired thickness)
                 relief='groove',    # Set relief style
                 bg='white',        # Background color of the label
                 fg='grey')        # Text color

label1.place(x=20, y=400)
label = tk.Label(a, 
                 text="""                                                    


















                                                                                                                                                     """, 
                 bd=1,              # Set border width (change to desired thickness)
                 relief='solid',    # Set relief style
                 bg='white',        # Background color of the label
                 fg='grey')        # Text color

label.place(x=614, y=450)
total=0
ite=tk.Label(a,padx=10,pady=7,text=f'({Id}) Items                                                       ₹ {(total):.2f}',font=('cambria',15),bg=b)
ite.place(x=640,y=470)
cg=tk.Label(a,padx=10,pady=7,text=f'CGST 5%                                                    + ₹ {(0.05*total):.2f}',font=('cambria',15),bg=b,fg='green')
cg.place(x=640,y=520)
sg=tk.Label(a,padx=10,pady=7,text=f'SGST 5%                                                    + ₹ {(0.05*total):.2f}',font=('cambria',15),bg=b,fg='green')
sg.place(x=640,y=570)
dis=tk.Label(a,padx=10,pady=7,text=f'Discount                                                    - ₹ {(0.03*total):.2f}',font=('cambria',15),bg=b,fg='red')
dis.place(x=640,y=620)
Total=tk.Label(a,padx=10,pady=7,text=f'Total Amount                                  ₹ {(total+(2*(0.05*total))-(0.03*total)):.2f}',font=('cambria',16,'bold'),bg=b)
Total.place(x=630,y=670)
def get(Event):
    sel=tv.focus()
    data=tv.item(sel)
    print(data)
    global row
    row=data['values']
    msg=f"""
    Coustomer Name : {row[1]}
    Phone Number  : {row[2]}
    Amount : {row[3]}"""
    messagebox.showinfo("Alert",msg)
    u.delete(0,END)
    u.insert(0,row[1])
    c.delete(0, END)
    c.insert(0, row[2])
    f.delete(0,END)
    f.insert(0,row[1])

def clear():
    u.delete(0, tk.END)
    c.delete(0, tk.END)
    f.delete(0, tk.END)
def insert(name,age,city):
    now = datetime.now()
    formatted_date = now.strftime("%d/%m/%Y")
    formatted_time = now.strftime("%I:%M %p")
    if u.get()=="" or  c.get()=="":
        messagebox.showinfo("Alert","Please Fill out the Details")
    else:
        qry="insert into users (name,father_name,city,date,time) values (?,?,?,?,?);"
        cur.execute(qry,(name,age,city,formatted_date,formatted_time))
        con.commit()
        messagebox.showinfo("Alert","Data Stored Successfully")
        clear()
        select()
        clear_item()
def add():
    global ite
    global total
    global Id
    global clear_item
    def appe(p_n,p_p,p_q):
        global total
        global Id
        Id+=1
        ID.append(Id)
        name.append(p_n)
        qty.append(int(p_q))
        price.append(float(p_p))
        select1(ID,name,qty,price)
        text_box.delete(0, tk.END)
        text_box.config(state='normal')
        text_box.delete(0, tk.END)
        text_box.insert(0,f" ₹ {total:.2f}")
        text_box.config(state='readonly',bg='white')
        clear()
    def bring_to_front():
        c.lift()
        c.attributes('-topmost', True)
        c.attributes('-topmost', False)
    def clear():
        p_n.delete(0, tk.END)
        p_p.delete(0, tk.END)
        p_q.delete(0, tk.END)
        p_n.focus()
    def remove_pro(nam):
        global Id
        ind=name.index(nam)
        ID.pop()
        name.pop(ind)
        qty.pop(ind)
        price.pop(ind)
        Id-=1
        select1(ID,name,qty,price)
        clear()
    def clear_item():
        Id=0
        ID=[]
        name=[]
        qty=[]
        price=[]
        t.delete(*t.get_children())
        select1(ID,name,qty,price)
    def select1(ID,name,qty,price):
        global ite
        global total
        t.delete(*t.get_children())
        total=0
        for i in range(len(ID)):
            t.insert("",END,values=[ID[i],name[i],qty[i],f"₹{price[i]:.2f}",f"₹{qty[i]*price[i]:.2f}"])
            total+=qty[i]*price[i]
        text_box.config(state='normal')
        text_box.delete(0, tk.END)
        text_box.insert(0,f" ₹ {total:.2f}")
        text_box.config(state='readonly',bg='white')
        ite.config(text=f'({Id}) Items                                                       ₹ {(total):.2f}')
        cg.config(text=f'CGST 5%                                                    + ₹ {(0.05*total):.2f}')
        sg.config(text=f'SGST 5%                                                    + ₹ {(0.05*total):.2f}')
        dis.config(text=f'Discount                                                    - ₹ {(0.03*total):.2f}')
        Total.config(text=f'Total Amount                                  ₹ {(total+(2*(0.05*total))-(0.03*total)):.2f}')
    def get_p(Event):
        sel=t.focus()
        data=t.item(sel)
        global row
        row=data['values']
        global num
        num=row[0]
        num=ID.index(num)
        p_n.delete(0,END)
        p_n.insert(0,row[1])
        p_q.delete(0, END)
        p_q.insert(0, row[2])
        p_p.delete(0, END)
        p_p.insert(0, str(row[3])[1:])
        bring_to_front()
    def update():
        name[num]=p_n.get()
        qty[num]=int(p_q.get())
        price[num]=float(p_p.get())
        select1(ID,name,qty,price)
    c=tk.Tk()
    c.geometry('500x300+1120+60')
    c.config(bg='white')
    colo='white'
    Label(c,padx=10,pady=7,text='',font=('cambria',16),bg=colo).grid(row=0,column=0,sticky='w')
    Label(c,padx=10,pady=7,text='Product Name',font=('cambria',16),bg=colo).grid(row=1,column=1,sticky='w')
    p_n=Entry(c,width=20,bd=1, relief="solid",font=('cambria',14))
    p_n.grid(row=1,column=2)
    Label(c,padx=10,pady=7,text='Product Quantity  ',font=('cambria',16),bg=colo).grid(row=2,column=1,sticky='w')
    p_q=Entry(c,width=20,bd=1, relief="solid",font=('cambria',14))
    p_q.grid(row=2,column=2)
    Label(c,padx=10,pady=7,text='Product Price',font=('cambria',16),bg=colo).grid(row=3,column=1,sticky='w')
    p_p=Entry(c,width=20,bd=1, relief="solid",font=('cambria',14))
    p_p.grid(row=3,column=2)
    Button(c,text="Add",font=('cambria',12),bg='#C1FA4A',border=0,width=13,command=lambda : appe(p_n.get(),p_p.get(),p_q.get())).place(x=30,y=200)
    Button(c,text="Update",font=('cambria',12),bg='#DB66F4',border=0,width=13,command=update).place(x=180,y=200)
    Button(c,text="Delete",font=('cambria',12),bg='#F26B79',border=0,width=13,command=lambda:remove_pro(p_n.get())).place(x=330,y=200)
    #----------------------------
    tre=Frame(a,bg="#ecf8f1")
    tre.place(x=50,y=450,width=500,height=300)
    s=ttk.Style()
    s.configure("my.Treeview",font=("cambria",13),rowheight=50)
    s.configure("my.Treeview.Heading",font=("cambria",13),rowheight=50)
    t=ttk.Treeview(tre,columns=(1,2,3,4,5),style='my.Treeview')
    t.heading("1",text=" Sl.No  ")
    t.column("1" , width=30)
    t.heading("2",text=" Product Name")
    t.column("2" , width=100)
    t.heading("3",text=" Qty")
    t.column("3" , width=50)
    t.heading("4",text=" Price")
    t.column("4" , width=50)
    t.heading("5",text=" Amount")
    t.column("5" , width=50)
    t['show']='headings'
    t.bind("<ButtonRelease-1>",get_p)
    Label(a,padx=10,pady=7,text='Total Amount',font=('cambria',16),bg=b).place(x=250,y=752)
    text_box = Entry(a, width=13, bd=1,bg='white', relief="solid", font=('cambria', 14))  # Light 2D border
    text_box.insert(0,f" ₹ {total}")
    text_box.config(state='readonly')
    text_box.place(x=400,y=760)
    t.pack(fill=X)
    #-----------------------------
    p_n.focus()
    bring_to_front()
    select1(ID,name,qty,price)
    c.mainloop()
def delete(name):
    qry="delete from users where name=?;"
    cur.execute(qry,(name,))
    con.commit()
    messagebox.showinfo("Alert","Datas Deleted Successfully")
    clear()
    select()
def update(name,age,city,Id):
    now = datetime.now()
    formatted_date = now.strftime("%d/%m/%Y")
    formatted_time = now.strftime("%I:%M %p")
    qry="update users set name=?,father_name=?,city=?,date=?,time=? where name=?"
    cur.execute(qry,(name,age,city,formatted_date,formatted_time,Id))
    con.commit()
    clear()
    select()
def select():
    tv.delete(*tv.get_children())
    qry="select * from users"
    cur.execute(qry)
    rows=cur.fetchall()
    for i in rows:
        tv.insert("",END,values=i)
def predect(d):
    plt.title(f"The Prediction of Products Sale on : {d}")
    da=d[:2]+"-"+d[3:5]+"-"+d[6:9]
    da+='3'
    products=df[da][:3]
    products=list(products)
    pro_name=df['Products'][:3]
    pro_name=list(pro_name)
    plt.bar(pro_name,products,color=['red','green','yellow'],label=['Biscuit','cashew','Detergent'])
    plt.ylim(0,140)
    plt.xlabel("Name of the Products")
    plt.ylabel("No of Products will be sell")
    plt.legend()
    dat.delete(0,tk.END)
    plt.show()
    plt.close()
a.geometry("1250x700+130+45")
a.state('zoomed')
u=StringVar()
c=StringVar()
b="white"
a.config(bg=b)
Label(a,text='                       SANDEEP SUPERMARKET',padx=10,pady=7,font=('cambria',18),bg=b,fg='Black').grid(row=0,column=2,sticky='w')#n, e, s, and/or w
Label(a,padx=10,pady=7,text='Customer Name',font=('cambria',16),bg=b).grid(row=1,column=0,sticky='w')
Label(a,padx=10,pady=7,text='Phone No',font=('cambria',16),bg=b).place(x=30,y=100)
Label(a,padx=10,pady=7,text='',font=('cambria',16),bg=b).grid(row=4,column=0,sticky='w')
u = Entry(a, width=28, bd=1, relief="solid", font=('cambria', 14))  # Light 2D border
u.grid(row=1, column=1)

c = Entry(a, width=28, bd=1, relief="solid", font=('cambria', 14))  # Light 2D border
c.place(x=167,y=110)

f = Entry(a, width=28, bd=1, relief="solid", font=('cambria', 14),show='*')  # Light 2D border
f.grid(row=4, column=1,pady=10)
f.grid_forget()
Button(a,text="Add item",font=('cambria',12),bg='#C1FA4A',border=0,width=20,command=add).grid(row=1,column=2)
Label(a,bg=b).grid(row=5,column=0)

Button(a,text="Submit Bill",font=('cambria',12),bg='#C1FA4A',border=0,width=20,command=lambda :insert(u.get(),c.get(),total)).place(x=30,y=260)
Button(a,text="Submit Bill",font=('cambria',16,'bold'),bg='#C1FA4A',border=0,width=37,command=lambda :insert(u.get(),c.get(),total)).place(x=612,y=770)
Button(a,text="Remove Bill",font=('cambria',12),bg='#F26B79',border=0,width=20,command=lambda :delete(u.get())).place(x=280,y=260)
Button(a,text="Update Bill",font=('cambria',12),bg='#DB66F4',border=0,width=20,command=lambda :update(u.get(),c.get(),total,f.get())).place(x=530,y=260)
global ID,name,qty,price
Id=0
ID=[]
name=[]
qty=[]
price=[]
dat=tk.Entry(a, width=28, bd=1, relief="solid", font=('cambria', 14))
dat.place(x=1500,y=90)
Label(a,padx=10,pady=7,text="Date To Predict",font=('cambria',16),bg=b).place(x=1300,y=83)
Button(a,text="Predict Sale",font=('cambria',12),bg='#C1FA4A',border=0,width=37,command=lambda :predect(str(dat.get()))).place(x=1500,y=140)
#-------------------------------
tree=Frame(a,bg="#ecf8f1")
tree.place(x=1130,y=450,width=740,height=300)
s=ttk.Style()
s.configure("my.Treeview",font=("cambria",13),rowheight=50)
s.configure("my.Treeview.Heading",font=("cambria",13),rowheight=50)
tv=ttk.Treeview(tree,columns=(1,2,3,4,5,6),style='my.Treeview')
tv.heading("1",text="Bill No")
tv.column("1" , width=20)
tv.heading("2",text="Customer Name")
tv.column("2" , width=100)
tv.heading("3",text="Phone No")
tv.column("3",width=40)
tv.heading("4",text="Amount")
tv.column("4",width=30)
tv.heading("5",text="Date")
tv.column("5",width=30)
tv.heading("6",text="Time")
tv.column("6",width=30)
tv['show']='headings'
tv.bind("<ButtonRelease-1>",get)
tv.pack(fill=X)
select()
select()
a.mainloop()
