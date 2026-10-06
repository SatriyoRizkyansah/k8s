1. Dasar & Konsep
   [x] Install Minikube & paham cara jalankannya (minikube start)
   [x] Paham beda Control Plane (Master Node) dan Worker Node
   [x] Kuasai perintah dasar: kubectl get nodes dan kubectl cluster-info

====================================================
kubernetes mengolola banyak server, dibagi jadi 2 peran utama.

- Control plane (pusat kendali)
- Worker Node (pelaksana)

a. cek Informasi cluster - kubectl cluster-info
b. cek daftar node - kubectl get nodes
c. cek kesehatan kompnen minikube - minikube status

2. Workloads (Pod & Deployment)
   [x] Paham struktur dasar file YAML K8s (apiVersion, kind, spec)
   [x] Bisa buat dan jalankan Pod via YAML (kubectl apply -f)
   [x] Bisa buat Deployment dengan multiple replika
   [x] Paham cara me-restart atau scaling Pod (kubectl scale)
   [x] Kuasai cara debugging log: kubectl logs dan kubectl describe

3. Networking (Menghubungkan Aplikasi)
   [ ] Paham beda ClusterIP, NodePort, dan LoadBalancer
   [ ] Bisa buat Service agar aplikasi internal bisa saling komunikasi
   [ ] Bisa buka akses aplikasi K8s agar bisa dibuka di browser laptop

4. Konfigurasi (ConfigMap & Secret)
   [ ] Bisa buat ConfigMap untuk simpan Environment Variables (.env)
   [ ] Bisa buat Secret untuk simpan data sensitif/password
   [ ] Bisa menyambungkan ConfigMap & Secret ke dalam Deployment YAML

5. Storage (Menyimpan Data Database)
   [ ] Paham konsep PersistentVolume (PV) dan PersistentVolumeClaim (PVC)
   [ ] Bisa deploy database di K8s agar datanya tidak hilang saat Pod mati

6. Package Manager (Helm)
   [ ] Install Helm di lokal
   [ ] Paham cara kerja Helm Chart
   [ ] Bisa deploy aplikasi pakai Helm dan edit file values.yaml

7. Custom Image & Registry
   [ ] Bisa build Docker Image buatan sendiri
   [ ] Bisa load Docker Image lokal ke dalam Minikube (minikube image load)
   [ ] Bisa deploy aplikasi buatan sendiri ke Minikube

8. CI/CD ke K8s
   [ ] Menyiapkan Runner CI/CD lokal (GitLab Runner / GitHub Self-Hosted)
   [ ] Buat pipeline otomatis: Git Push ➔ Build Image ➔ Deploy ke Minikube
   [ ] Uji coba Rolling Update (update aplikasi tanpa downtime)
