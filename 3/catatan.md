# Catatan Belajar K8s - Poin 3: Networking (Menghubungkan Aplikasi)

## 1. Tiga Tipe Utama Service K8s

Service adalah pintu masuk jaringan yang memberikan alamat IP/DNS yang stabil di depan Pods.

| Tipe Service                | Lingkup Akses                     | Kegunaan Utama                                                                                                             |
| :-------------------------- | :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| **`ClusterIP`** _(Default)_ | **Internal Cluster saja**         | Komunikasi antar-aplikasi internal (Backend ➔ Database, Frontend ➔ Backend). Tidak bisa dibuka dari luar/browser.          |
| **`NodePort`**              | **Internal + Luar (Port Server)** | Membuka port khusus di rentang `30000-32767` pada IP Node/Server. Sangat cocok untuk pengujian lokal di Minikube.          |
| **`LoadBalancer`**          | **Publik / Internet**             | Mengintegrasikan K8s dengan Load Balancer resmi milik Cloud Provider (AWS, GCP, Azure) untuk mendapatkan IP Publik statis. |

---

## 2. Praktik Manifest Service YAML

### A. Service Internal (`ClusterIP`)

Digunakan agar aplikasi internal bisa saling panggil menggunakan nama DNS Service-nya (contoh panggil via code: `http://backend-service:3000`).

```yaml
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  type: ClusterIP
  selector:
    app: backend-app # Mengarah ke Pod dengan label "app: backend-app"
  ports:
    - port: 3000 # Port internal Service
      targetPort: 3000 # Port container di dalam Pod
```
