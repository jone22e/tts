# Kokoro TTS via Docker Compose (GPU NVIDIA)

Pacote mínimo para subir o Kokoro TTS com GPU NVIDIA usando apenas Docker Compose.

## Requisitos

- Docker e Docker Compose instalados
- NVIDIA Container Toolkit configurado no host
- GPU NVIDIA compatível

Teste antes:

```bash
nvidia-smi
docker run --rm --gpus all nvidia/cuda:12.3.1-base-ubuntu22.04 nvidia-smi
```

Se os dois comandos funcionarem, a GPU está pronta para containers.

## Subir

Dentro da pasta deste arquivo:

```bash
docker compose up -d
```

## Ver logs

```bash
docker compose logs -f
```

## Parar

```bash
docker compose down
```

## Testar no navegador

Abra:

- API/UI: http://SEU-IP:8880/web
- Docs: http://SEU-IP:8880/docs

## Teste rápido por curl

```bash
curl http://localhost:8880/health
```

Se esse endpoint não existir na versão atual, abra `/docs` e teste por lá.

## Observações

- Este pacote usa a imagem oficial GPU do projeto Kokoro FastAPI.
- A porta exposta é `8880`.
- Se sua GPU for muito nova e houver incompatibilidade de CUDA/PyTorch, pode ser necessário trocar a tag da imagem ou usar uma imagem atualizada.
