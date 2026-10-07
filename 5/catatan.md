# Catatan Belajar K8s - Poin 5: Storage (PV & PVC)

## 1. Mengapa Butuh Storage di K8s?

Pod bersifat _ephemeral_ (sementara). Tanpa Volume, semua file & data database akan hilang terhapus jika Pod mati atau di-restart.

## 2. Beda PV vs PVC

| Objek                           | Peran & Fungsi                                                |
| :------------------------------ | :------------------------------------------------------------ |
| **PersistentVolume (PV)**       | Alokasi storage fisik/harddisk nyata yang disediakan cluster. |
| **PersistentVolumeClaim (PVC)** | Request/Izin sewa kapasitas storage oleh Pod/Aplikasi.        |

## 3. Cara Menghubungkan PVC ke Pod (Deployment)

1. Deklarasikan **PVC** dengan kapasitas yang dibutuhkan (contoh: `1Gi`).
2. Di `spec.volumes` Deployment, panggil `claimName: <nama-pvc>`.
3. Di `spec.containers.volumeMounts`, arahkan volume tersebut ke folder data internal container (contoh Postgres: `/var/lib/postgresql/data`).

---

## 4. Cheat Sheet Perintah CLI (`kubectl`)

- **Melihat daftar PVC:**
  ```bash
  kubectl get pvc
  ```
