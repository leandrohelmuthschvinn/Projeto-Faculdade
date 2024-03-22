# Projeto-Faculdade
import tkinter as tk
from tkinter import messagebox , ttk


class Cliente:
    def __init__(self, nome, email, telefone, cpf):
        self.nome = nome
        self.email = email
        self.telefone = telefone
        self.cpf = cpf

class SistemaCadastro:
    def __init__(self):
        self.cliente = []

    def cadastrar(self, nome, email, telefone, cpf):
        vCliente = self.buscar(nome)
        if vCliente == None:
            cliente = Cliente(nome, email, telefone, cpf)
            self.cliente.append(cliente)
        else:
            print("cliente ja cadastrado")

    def buscar(self, nome):
        for cliente in self.cliente:
            if cliente.nome == nome:
                return cliente
            return None
            
                 

class App:
    def __init__(self, root):
        self.root = root
        self.sistema = SistemaCadastro()

        self.nome_label = ttk.Label(root, text="Nome")
        self.nome_label.configure(font=("Arial", 20), anchor="center")
        self.nome_entry = ttk.Entry(root)
        self.nome_entry.configure(font=("Arial", 20))
        self.email_label = ttk.Label(root, text="Email")
        self.email_label.configure(font=("Arial", 20), anchor="center")
        self.email_entry = ttk.Entry(root)
        self.email_entry.configure(font=("Arial", 20))
        self.telefone_label = ttk.Label(root, text="Telefone")
        self.telefone_label.configure(font=("Arial", 20), anchor="center")
        self.telefone_entry = ttk.Entry(root)
        self.telefone_entry.configure(font=("Arial", 20))
        self.cpf_label = ttk.Label(root, text="Cpf")
        self.cpf_label.configure(font=("Arial", 20), anchor="center")
        self.cpf_entry = ttk.Entry(root)
        self.cpf_entry.configure(font=("Arial", 20))
        self.cadastrar_button = ttk.Button(root, text="Cadastrar", command=self.cadastrar) 
        self.buscar_button = ttk.Button(root, text="Buscar", command=self.buscar) 
           


        self.nome_label.pack()
        self.nome_entry.pack()
        self.email_label.pack()
        self.email_entry.pack()
        self.telefone_label.pack()
        self.telefone_entry.pack()
        self.cpf_label.pack()
        self.cpf_entry.pack()
        self.cadastrar_button.pack()
        self.buscar_button.pack()


    def cadastrar(self):
        nome = self.nome_entry.get()
        email = self.email_entry.get()
        telefone = self.telefone_entry.get()
        cpf = self.cpf_entry.get()
        self.sistema.cadastrar(nome, email, telefone, cpf)   
        messagebox.showinfo("Sucesso", "Cliente cadastrado com sucesso! ")   

    def buscar(self):
        nome = self.nome_entry.get()
        cliente = self.sistema.buscar(nome)
        if cliente:
            messagebox.showinfo("Cliente encontrado", f"Nome: {cliente.nome}, Email: {cliente.email}, Telefone: {cliente.telefone}, CPF: {cliente.cpf}")
        else:    
            messagebox.showinfo("Cliente nao encontrado!")    

root = tk.Tk()
root.geometry("800x600")
app = App(root)
root.mainloop()
