# Install Grafana Alloy (Ansible)

Playbook ini sudah disiapkan agar password tidak disimpan di `install-alloy.yml`.
Gunakan `group_vars` atau `host_vars` dan enkripsi dengan Ansible Vault, cocok untuk eksekusi dari AWX.

## Lokasi Variabel Secret

- `alloy_prometheus_password`
- `alloy_loki_password`

Contoh file tersedia di:

- `group_vars/all/alloy-secrets.yml.example`

## Rekomendasi Dengan Vault

1. Salin contoh file:
	`cp group_vars/all/alloy-secrets.yml.example group_vars/all/alloy-secrets.yml`
2. Isi nilainya.
3. Enkripsi file:
	`ansible-vault encrypt group_vars/all/alloy-secrets.yml`
4. Di AWX, tambahkan Vault Credential agar job template bisa dekripsi file Vault.

## Opsi Host Spesifik

Jika password berbeda per host, simpan di `host_vars/<hostname>.yml` (juga terenkripsi Vault).
