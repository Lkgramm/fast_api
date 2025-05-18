# 🧠 ML Model Serving

## 🚀 Описание

REST API для выполнения инференса модели машинного обучения, реализованное на **FastAPI**.  
Принимает изображение и возвращает результат сегментации в виде цветной маски.

![Пример сегментации: оригинальное изображение](docs/origin.jpg)
![Результат обработки](docs/mask.jpg)

## 🤖 Используемая модель

- **Модель**: `UperNetForSemanticSegmentation` (Hugging Face)
- **Бэкбон**: `ConvNeXt-tiny`
- **Датасет**: обучена на ADE20K (150 классов)
- **Описание**: сверточная сеть для семантической сегментации сценических изображений

🔗 [https://huggingface.co/openmmlab/upernet-convnext-tiny](https://huggingface.co/openmmlab/upernet-convnext-tiny)

## 🛠 Технологии

- FastAPI
- PyTorch
- Transformers (Hugging Face)
- PIL / NumPy
- FastAPI Docs (Swagger UI)

## 📦 Установка

```bash
poetry install
```

## ▶️ Запуск

```bash
make dev
```

API будет доступно по адресу:  
👉 http://localhost:8000  
Swagger UI: http://localhost:8000/docs

## 🌐 API Endpoints

| Метод | Путь        | Описание |
|-------|-------------|----------|
| GET   | `/health`   | Проверка работоспособности сервиса |
| POST  | `/segment`  | Принимает изображение, возвращает маску сегментации |

## 🖼 Пример использования

```bash
curl -X POST "http://localhost:8000/segment" \
     -H "accept: image/png" \
     -H "Content-Type: multipart/form-data" \
     -F "file=@your_image.jpg" \
     --output segmented_mask.png
```
