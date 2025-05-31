# LAB 2 — Programowanie Aplikacji w Chmurze Obliczeniowej

## 📌 Cel

Automatyczne budowanie i publikacja obrazu kontenera Docker na podstawie aplikacji z zadania 1. Obraz publikowany jest do GitHub Container Registry (GHCR) po wcześniejszym sprawdzeniu bezpieczeństwa (CVE).

## ✅ Co robi pipeline:

1. Buduje obraz na platformy: `linux/amd64` i `linux/arm64`
2. Używa cache z DockerHub (`mode=max`)
3. Weryfikuje bezpieczeństwo obrazu za pomocą **Trivy**
4. Publikuje obraz do `ghcr.io` tylko jeśli nie zawiera **CRITICAL** ani **HIGH** zagrożeń

## 🧪 Tagowanie

- `latest` – najnowszy build
- `sha-<commit>` – unikalny tag na podstawie SHA
- Cache: `docker.io/<dockerhub-user>/cloud-lab2-cache:latest`

## 🔐 Wymagane Secrets:

Dodaj w repozytorium (Settings > Secrets and variables > Actions):

- `GHCR_PAT` – token GitHub z uprawnieniami `write:packages`
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN` – wygenerowany token do logowania się na DockerHub

## 🚀 Uruchomienie

Po zacommitowaniu do gałęzi `main`, workflow zbuduje i wypchnie obraz.

