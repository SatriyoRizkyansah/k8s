# Catatan Belajar K8s - Poin 4: Konfigurasi (ConfigMap & Secret)

## 1. Perbedaan ConfigMap vs Secret

| Objek         | Peran & Keamanan                                      | Contoh Penggunaan                         |
| :------------ | :---------------------------------------------------- | :---------------------------------------- |
| **ConfigMap** | Menyimpan data konfigurasi non-sensitif (Plain Text). | `PORT`, `APP_ENV`, `DB_HOST`, `LOG_LEVEL` |
| **Secret**    | Menyimpan data sensitif/rahasia (Base64 / Encrypted). | `DB_PASSWORD`, `API_KEY`, `JWT_SECRET`    |

---

## 2. Cara Inject ke Deployment YAML

Gunakan blok `envFrom` di bawah spesifikasi container untuk mengimpor seluruh variabel sekaligus:

```yaml
spec:
  containers:
    - name: my-app
      image: node:22-alpine
      envFrom:
        - configMapRef:
            name: app-config
        - secretRef:
            name: app-secret
```
