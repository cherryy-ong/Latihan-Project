import tkinter as tk
from tkinter import ttk, messagebox

root = tk.Tk()
root.title("Aplikasi Entri Nilai Siswa")
root.geometry("600x600")

data = []

def tampilkan(frame):
    frame.tkraise()

def refresh_treeview(target_tree, data_source):
    for item in target_tree.get_children():
        target_tree.delete(item)
        
    for row in data_source:
        target_tree.insert('', tk.END, values=row)

def muncul():
    nama = entry_nama.get().strip()
    kelas = entry_kelas.get().strip()
    alamat = entry_alamat.get().strip()

    if not nama or not kelas or not alamat:
        messagebox.showerror("Error", "Semua kolom harus diisi!")
        return 
        
    new_tuple = (nama, kelas, alamat) 
    data.append(new_tuple)
    
    entry_nama.delete(0, tk.END)
    entry_kelas.delete(0, tk.END)
    entry_alamat.delete(0, tk.END)
    
    messagebox.showinfo("Sukses", f"Data {nama} berhasil disimpan!")
    
def lihat_data_dan_pindah():
    refresh_treeview(tree_hal2, data)
    tampilkan(hal2)
    
def cari_data():
    nama_dicari = entry_cari_nama.get().strip().lower()
    hasil_pencarian = []
    
    if not nama_dicari:
        refresh_treeview(tree_hal3, data)
        return
        
    for row in data:
        if nama_dicari in row[0].lower():
            hasil_pencarian.append(row)

    refresh_treeview(tree_hal3, hasil_pencarian)

hal1 = tk.Frame(root,bg='#fff9e3')

label_judul=tk.Label(hal1,text="Nama Lengkap:")
label_judul.pack(pady=(5, 0))
entry_nama=tk.Entry(hal1, width=30)
entry_nama.pack(pady=2)

label_judul2=tk.Label(hal1,text="Kelas:")
label_judul2.pack(pady=(5, 0))
entry_kelas=tk.Entry(hal1, width=30)
entry_kelas.pack(pady=2)

label_judul3=tk.Label(hal1,text="Alamat:")
label_judul3.pack(pady=(5, 0))
entry_alamat=tk.Entry(hal1, width=30) 
entry_alamat.pack(pady=2)

btn1=tk.Button(hal1,text="Simpan Data", command=muncul, font=("Arial", 10, "bold"))
btn1.pack(pady=15)

btn3=tk.Button(hal1,text="Lihat Semua Data", command=lihat_data_dan_pindah)
btn3.pack(pady=5)

btn4=tk.Button(hal1,text="Cari Data", command=lambda: tampilkan(hal3)) 
btn4.pack(pady=5)

hal2 = tk.Frame(root,bg='#fff9e3')

columns_hal2 = ('nama', 'kelas', 'alamat')
tree_hal2 = ttk.Treeview(hal2, columns=columns_hal2, show='headings', height=10) 
tree_hal2.heading('nama', text='Nama')
tree_hal2.heading('kelas', text='Kelas')
tree_hal2.heading('alamat', text='Alamat')
tree_hal2.column('nama', width=150, anchor='w') 
tree_hal2.column('kelas', width=70, anchor='center')
tree_hal2.column('alamat', width=150, anchor='w') 
tree_hal2.pack(padx=10, fill='x')

btn2=tk.Button(hal2,text="Kembali", command=lambda: tampilkan(hal1))
btn2.pack(pady=20)


hal3 = tk.Frame(root, bg='#fff9e3')

tk.Label(hal3, text="Cari Data Siswa", font=("Arial", 18, "bold"), bg='#fff9e3').pack(pady=30)

tk.Label(hal3, text="Masukkan Nama:", bg='#fff9e3').pack(pady=(10, 0))
entry_cari_nama=tk.Entry(hal3, width=30, font=("Arial", 12))
entry_cari_nama.pack(pady=5)

btn_cari=tk.Button(hal3, text="Cari", command=cari_data, font=("Arial", 10, "bold"), 
                   relief=tk.RAISED, borderwidth=2)
btn_cari.pack(pady=10)

columns_hal3 = ('nama', 'kelas', 'nilai')
tree_hal3 = ttk.Treeview(hal3, columns=columns_hal3, show='headings', height=10) 

tree_hal3.heading('nama', text='Nama')
tree_hal3.heading('kelas', text='Kelas')
tree_hal3.heading('nilai', text='Alamat')

tree_hal3.column('nama', width=150, anchor='w') 
tree_hal3.column('kelas', width=70, anchor='center')
tree_hal3.column('nilai', width=150, anchor='w') 

tree_hal3.pack(padx=10, pady=20, fill='x')

btn_kembali_hal3=tk.Button(hal3, text="Kembali", command=lambda: tampilkan(hal1))
btn_kembali_hal3.pack(pady=20)

for frame in (hal1, hal2, hal3): 
    frame.place(x=0,y=0,relwidth=1,relheight=1)

tampilkan(hal1)

root.mainloop()
