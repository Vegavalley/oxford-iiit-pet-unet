# oxford-iiit-pet-unet

Этот проект реализует U-Net для семантической сегментации изображений из Oxford-IIIT Pet Dataset на базе весов предобученной CNN для CIFAR-10.

## Особенности
- **Датасет**: Oxford-IIIT Pet Dataset (2944 тренировочных, ~736 валидационных, ~3666 тестовых изображений, размер 128x128).
- **Модель**: U-Net с 367,940,235 параметрами, дообученная с разморозкой слоёв `conv2d_8`–`conv2d_11`.
- **Метрики**:
  - MeanIoU: 0.7405
  - IoU по классам:
    - Background: 0.8673
    - Animal: 0.8775
    - Border: 0.7132
  - Validation Accuracy: 0.9041
- **Технологии**: TensorFlow 2.17.0, Python 3.10, NumPy, Matplotlib, Pandas.
- **Аугментации**: Повороты, сдвиги, зум, изменение яркости.


## Использование
Скачайте датасет или используйте предобработанные файлы (см. раздел Данные).
Поместите данные в папку проекта или укажите пути в скрипте.
Запустите обучение: python src/unet_augmentation_finetune_corrected_v10.py
Результаты (история, визуализации) сохраняются в папке results/.

## Данные (https://drive.google.com/drive/folders/1RbAnVXkQ0jKflNS8Hxg_YHu-v23q_vW8?usp=share_link)
**Датасет**: Oxford-IIIT Pet доступен через TensorFlow Datasets.
**Предобработанные файлы (размер ~1.5 ГБ, размещены на Google Drive)**:
- train_images_corrected.npy
- train_masks_corrected.npy
- val_images_corrected.npy
- val_masks_corrected.npy
- test_images_corrected.npy
- test_masks_corrected.npy
**Модель**:
- best_unet_oxford_pet_v1.keras (~1.37 ГБ).
- Примечание: Загрузите файлы и укажите их пути в скрипте или используйте preprocess для обработки датасета с нуля.


## Результаты
**Метрики:**
- Лучшая валидационная точность: 90.41%.
 - MeanIoU: 0.7405 (близко к SOTA для U-Net).
**Визуализации:** Примеры сегментации сохранены в results/oxford_pet_visualization_v1_{i}.png.
**История обучения:** См. results/unet_oxford_pet_history_v10.csv.
