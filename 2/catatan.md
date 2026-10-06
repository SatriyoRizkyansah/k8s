# Catatan Belajar K8s - Poin 2: Workloads (Pod & Deployment)

## 1. Anatomi & Struktur Dasar File YAML K8s

Setiap file manifest Kubernetes selalu memiliki 4 komponen utama:

- **`apiVersion`**: Versi API yang digunakan K8s (contoh: `v1`, `apps/v1`).
- **`kind`**: Jenis objek yang dibuat (contoh: `Pod`, `Deployment`, `Service`).
- **`metadata`**: Identitas objek (seperti `name` dan `labels`).
- **`spec`**: Spesifikasi teknis (seperti jumlah replika, container image, port, dll).

---

## 2. Perbedaan Pod, Deployment, dan Service

| Objek          | Peran & Fungsi Utama                                                                                                                       |
| :------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| **Pod**        | Unit terkecil di K8s tempat container (aplikasi) berjalan. Sifatnya _ephemeral_ (sementara) dan IP-nya berubah-ubah jika _restart_.        |
| **Deployment** | Pengawas/mandor yang mengelola Pods. Menjaga jumlah replika, melakukan _auto-healing_ jika Pod mati, dan menangani _zero-downtime update_. |
| **Service**    | Pintu gerbang jaringan dengan IP/DNS permanen di depan Pods yang bertugas membagi beban trafik (_load balancer_).                          |

---

## 3. Praktik Manifest YAML (`deployment.yaml`)

Pod tidak perlu dibuatkan file YAML tersendiri karena spesifikasinya sudah dibungkus di dalam **Deployment** (`spec.template`).

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3 # Menjaga selalu ada 3 Pod aktif
  selector:
    matchLabels:
      app: nginx-app
  template: # Spesifikasi Pod
    metadata:
      labels:
        app: nginx-app
    spec:
      containers:
        - name: nginx
          image: nginx:alpine
          ports:
            - containerPort: 80
```
