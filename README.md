# human-detection
# Установка
Для установки проекта необходимо скачать 
* tensorflow-human-detection.py или tensorflow-human-detection-with-mapping.py
* [Модель для проекта faster rcnn inception v2 coco] (http://download.tensorflow.org/models/object_detection/faster_rcnn_inception_v2_coco_2018_01_28.tar.gz)
# Необходимые модули
```
* Tensorflow или Tensorflow-gpu последней версии
* Opencv2
```
# Запуск проекта
* Для начала нужно создать проект и разархивировать туда модель faster rcnn inception v2 coco из файла faster_rcnn_inception_v2_coco_2018_01_28.tar.gz (можно использовать и свою модель подходящую под проект).
* В папку проекта также нужно положить файл tensorflow-human-detection.py или tensorflow-human-detection-with-mapping.py
* Для запуска обработки видео, нужно видео, для примера можно взять отсюда 
(http://www.robots.ox.ac.uk/~lav/Research/Projects/2009bbenfold_headpose/Datasets/TownCentreXVID.avi) 

В коде файла .py проверить правильное расположение папки, где находится ваша модель и видео
```
model_path = '/path/to/model/faster_rcnn_inception_v2_coco_2018_01_28/frozen_inference_graph.pb'
cap = cv2.VideoCapture('/path/to/video/TownCentreXVID.avi')
```
Если вы устанавливаете версию с маппингом вам потребуется иметь план помещения, для того чтобы правильно производилась гомография, а также настроить совпадения точек на изображении камеры и вашего плана
```
pts_src = np.array([[x1_camera, y1_camera], [x2_camera, y2_camera], [x3_camera, y3_camera], [x4_camera, y4_camera]])                
pts_dst = np.array([[x1_plan, y1_plan], [x2_plan, y2_plan], [x3_plan, y3_plan], [x4_plan, y4_plan]])
```
А так же указать путь для сохранения плана с нанесенной точкой
```
im_dst = cv2.imread('/path/to/test plan.jpg')
cv2.imwrite('/path/to/test plan.jpg', im_dst)
```
После того как всё скачено, установлено и перепроверено можно запускать .py файл. Для выхода из окна работы программы нужно нажать Q.
