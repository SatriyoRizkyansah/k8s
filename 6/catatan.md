# Catatan Belajar K8s - Poin 6: Package Manager (Helm)

## 1. Perintah Dasar Helm CLI

| Perintah                                     | Fungsi                                                            |
| :------------------------------------------- | :---------------------------------------------------------------- |
| `helm create <nama-chart>`                   | Membuat struktur folder Helm Chart baru.                          |
| `helm install <nama-release> <folder-chart>` | Deploy Helm Chart ke cluster K8s.                                 |
| `helm list`                                  | Melihat daftar aplikasi (release) yang sedang berjalan via Helm.  |
| `helm upgrade <nama-release> <folder-chart>` | Menerapkan perubahan variabel pada `values.yaml`.                 |
| `helm uninstall <nama-release>`              | Menghapus seluruh resource K8s yang dibungkus oleh Helm tersebut. |
| `helm rollback <nama-release> <revisi>`      | Membatalkan deployment dan kembali ke versi revisi sebelumnya.    |

---

## 2. Alur Kerja File di Helm Chart

1. Tulis template YAML di dalam folder `templates/`.
2. Gunakan sintaks variabel `{{ .Values.<nama_variabel> }}` pada manifest YAML.
3. Deklarasikan nilai variabel tersebut di file `values.yaml`.
4. Jalankan `helm install` atau `helm upgrade`.
