import tkinter as tk
from tkinter import ttk

def tampilkan_input():
    label_nilai_asli.grid(row=1, column=0, sticky=tk.W, pady=10)
    entry_nilai_asli.grid(row=1, column=1, pady=10)
    label_skala_asli.grid(row=2, column=0, sticky=tk.W, pady=10)
    entry_skala_asli.grid(row=2, column=1, pady=10)
    label_skala_target.grid(row=3, column=0, sticky=tk.W, pady=10)
    entry_skala_target.grid(row=3, column=1, pady=10)
    tombol_hitung.grid(row=4, columnspan=2, pady=20)
    tombol_mulai.grid_forget()

def hitung_skala():
    try:
        nilai_asli = float(entry_nilai_asli.get())
        skala_asli = float(entry_skala_asli.get())
        skala_target = float(entry_skala_target.get())
        hasil = nilai_asli * (skala_target / skala_asli)
        label_hasil.config(text=f"Ukuran dalam skala target: {hasil:.2f} cm")
        label_hasil.grid(row=5, columnspan=2, pady=10)
    except ValueError:
        label_hasil.config(text="Masukkan nilai numerik yang valid")

root = tk.Tk()
root.title("Kalkulator Skala Gambar Kerja")
root.geometry("400x600")
root.configure(bg='#8B4513')

style = ttk.Style()
style.configure('TFrame', background='#8B4513')
style.configure('TLabel', background='#8B4513', foreground='#FFFFFF', font=('Helvetica', 16))
style.configure('TEntry', font=('Helvetica', 16))
style.configure('TButton', background='#8B0000', foreground='black', font=('Helvetica', 16), padding=10)

frame_utama = tk.Frame(root, bg='#8B4513')
frame_utama.place(relx=0.5, rely=0.5, anchor=tk.CENTER)

label_judul = tk.Label(frame_utama, text="Kalkulator Skala Gambar Kerja", bg='#8B4513', fg='#FFFFFF', font=('Helvetica', 20, 'bold'))
label_judul.grid(row=0, columnspan=2, pady=(0, 20))

label_nilai_asli = ttk.Label(frame_utama, text="Nilai Asli (cm):")
entry_nilai_asli = ttk.Entry(frame_utama, width=20)
label_skala_asli = ttk.Label(frame_utama, text="Skala Asli:")
entry_skala_asli = ttk.Entry(frame_utama, width=20)
label_skala_target = ttk.Label(frame_utama, text="Skala Target:")
entry_skala_target = ttk.Entry(frame_utama, width=20)

tombol_mulai = tk.Button(frame_utama, text="Mulai", command=tampilkan_input, font=('Helvetica', 16), relief='flat', padx=20, pady=10)
tombol_hitung = tk.Button(frame_utama, text="Hitung Ukuran Skala", command=hitung_skala, font=('Helvetica', 16), relief='flat', padx=20, pady=10)
label_hasil = ttk.Label(frame_utama, text="", background='#8B4513', foreground='#FFFFFF', font=('Helvetica', 16))

tombol_mulai.grid(row=4, columnspan=2, pady=20)


root.mainloop()
