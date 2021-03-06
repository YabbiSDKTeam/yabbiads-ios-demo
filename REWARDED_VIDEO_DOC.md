# Полноэкранный видео баннер с вознаграждением
Баннер показывается пользователю на весь экран, с возможностью закрыть баннер и перейти по рекламной ссылке.  
Когда пользователь досмотрит такую рекламу, он может получить вознаграждение

## Загрузка рекламы
Для загрузки рекламы используйте следующий код
```swift
YabbiAds.loadAd(AdType.REWARDED)
```

## Методы обратного вызова
Для работы с рекламой необходимо предоставить класс для передачи событий жизненного цикла рекламного контейнера.
Для инициализации рекламного контейнера выполните следующие действия:
```swift
YabbiAds.setRewardedDelegate(self)
```
Обычно класс, который работает с Полноэкранными объявлениями, одновременно является и классом делегата, поэтому в качестве свойства делегата можно указать self .
Теперь вы можете использовать следующие методы обратного вызова:

```swift
extension YourViewController: YabbiRewardedVideoDelegate {
    
    func onRewardedVideolLoaded() {
        // Вызывется при загрузке рекламы
    }

    func oRewardedVideoLoadFailed(_ error: String) {
        // Вызывется если при загрузке рекламы произошла ошибка
    }

    func onRewardedVideoShown() {
        //  Вызывается при показе рекламы
    }

    func onRewardedVideoShowFailed(_ error: String) {
         // Вызывется если при показе рекламы произошла ошибка
    }

    func onRewardedVideoClosed(_ error: String) {
        // Вызывается при закрытии рекламы
    }

    func onRewardedVideoFinished() {
        // Вызывется когда реклама закончилась
    }
}
```

## Проверка загрузки рекламы
Вы можете проверить статус загрузки перед работы с рекламой.
```swift
YabbiAds.isAdLoaded(AdType.REWARDED)
```

Рекомендуем всегда проверять статус загрузки рекламы, прежде чем пытаться ее показать.
```swift
if(YabbiAds.isAdLoaded(AdType.REWARDED)) {
    YabbiAds.showAd(AdType.REWARDED)
}
```

## Показ рекламы
Для показа рекламы используйте метод:
```swift
YabbiAds.showAd(AdType.REWARDED)
```

## Уничтожение рекламного контейнера
Для уничтожения рекламы добавьте следующий код в вашем приложении.
```swift
YabbiAds.destroyAd(AdType.REWARDED)
```