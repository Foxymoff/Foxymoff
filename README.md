import tkinter as tk
from tkinter import ttk
import math
from tkinter import messagebox

def calculate_roots():
    try:
        a = float(a_entry.get())
        b = float(b_entry.get())
        c = float(c_entry.get())

        if a == 0:
            messagebox.showerror("Ошибка", "Коэффициент 'a' не может быть равен нулю.")
            return
        
        discriminant = b**2 - 4*a*c

        if discriminant > 0:
            x1 = (-b + math.sqrt(discriminant)) / (2*a)
            x2 = (-b - math.sqrt(discriminant)) / (2*a)
            result_label.config(text=f"Корни: x1 = {x1:.2f}, x2 = {x2:.2f}")
        elif discriminant == 0:
            x = -b / (2*a)
            result_label.config(text=f"Один корень: x = {x:.2f}")
        else:
            real_part = -b / (2 * a)
            imaginary_part = math.sqrt(-discriminant) / (2 * a)
            result_label.config(text=f"Корни комплексные:\nx1 = {real_part:.2f} + {imaginary_part:.2f}i \nx2 = {real_part:.2f} - {imaginary_part:.2f}i")
            
    except ValueError:
        messagebox.showerror("Ошибка", "Введите корректные числовые значения.")

# Создание главного окна
root = tk.Tk()
root.title("Решатель квадратных уравнений")
root.geometry("400x300")

# Стиль ttk
style = ttk.Style()
style.configure("TButton", padding=6, relief="flat", background="#e0e0e0")
style.configure("TLabel", padding=4, font=("Arial", 10))

# Метки и поля ввода для коэффициентов a, b, c
a_label = ttk.Label(root, text="Коэффициент a:")
a_label.grid(row=0, column=0, padx=10, pady=10, sticky="e")
a_entry = ttk.Entry(root)
a_entry.grid(row=0, column=1, padx=10, pady=10)

b_label = ttk.Label(root, text="Коэффициент b:")
b_label.grid(row=1, column=0, padx=10, pady=10, sticky="e")
b_entry = ttk.Entry(root)
b_entry.grid(row=1, column=1, padx=10, pady=10)

c_label = ttk.Label(root, text="Коэффициент c:")
c_label.grid(row=2, column=0, padx=10, pady=10, sticky="e")
c_entry = ttk.Entry(root)
c_entry.grid(row=2, column=1, padx=10, pady=10)

# Кнопка для вычисления
calculate_button = ttk.Button(root, text="Вычислить", command=calculate_roots)
calculate_button.grid(row=3, column=0, columnspan=2, pady=20)

# Метка для вывода результата
result_label = ttk.Label(root, text="")
result_label.grid(row=4, column=0, columnspan=2, pady=10)

# Запуск главного цикла
root.mainloop()
<!---
Foxymoff/Foxymoff is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
