---
title: Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 15298414788c112c4f6a1f761055efd38933dfde
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751445"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika

Kodowane testy interfejsu użytkownika obejmuje obsługę, niektóre z formantów HTML5, które są dołączone do programu Internet Explorer 9 i programu Internet Explorer 10.

 **Wymagania**

-   Visual Studio Enterprise

> [!WARNING]
> W wersjach wcześniejszych niż program Internet Explorer 10 było możliwe do uruchomienia kodowanych testów interfejsu użytkownika w porównaniu do programu Internet Explorer wyższym poziomie uprawnień. Podczas uruchamiania kodowane testy interfejsu użytkownika w programie Internet Explorer 10, zarówno kodowanego testu interfejsu użytkownika, jak i programu Internet Explorer musi być na tym samym poziomie uprawnień. Jest to spowodowane bardziej bezpieczne funkcje kontenera aplikacji w programie Internet Explorer 10.


> [!WARNING]
> Jeśli tworzysz kodowanego testu interfejsu użytkownika w programie Internet Explorer 10, może nie zostać uruchomiony przy użyciu programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane programu Internet Explorer 10 zawiera formanty HTML5, takie jak Audio i wideo, ProgressBar oraz Slider. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.


## <a name="supported-html5-controls"></a>Formanty obsługiwanych języków HTML5.
 Kodowane testy interfejsu użytkownika obejmują obsługę rekordu, odtwarzania i sprawdzania poprawności następujących formantów HTML5:

-   [Audio Control](#UsingHTML5ControlsCodedUITestsAudio)

-   [Formant wideo](#UsingHTML5ControlsCodedUITestsVideo)

-   [Slider](#UsingHTML5ControlsCodedUITestsSlider)

-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)

###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Audio Control
 **Formant audio:** poprawnie zarejestrowana i odtwarzania akcji w formancie HTML5 Audio.

 ![Formant HTML5 Audio](../test/media/codedui_html5_audio.png)

|Akcja|Rejestrowanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Odtwórz dźwięk**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Odtwórz \<name > Audio od 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Wyszukiwanie się w określonym czasie, które usłyszysz**|Wyszukiwanie \<name > Audio do 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Wstrzymaj audio**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Wstrzymaj \<name > Audio na 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Wyciszenia audio**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Wyciszenia \<name > Audio|HtmlAudio.Mute()|
|**Włącz dźwięk**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Włącz \<name > Audio|HtmlAudio.Unmute()|
|**Zmień głośność dźwięku**|Ustaw wielkość \<name > Audio do 79%|HtmlAudio.SetVolume(float)|

 Następujące właściwości są dostępne dla HtmlAudio i na wszystkich z nich można dodać potwierdzenia:

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume

```

 **Wyszukiwanie właściwości:** właściwości wyszukiwania `HtmlAudio` są `Id`, `Name` i `Title`.

 **Właściwości filtru:** właściwości filtru `HtmlAudio` są `Src`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Czas wyszukiwania i Wstrzymaj może być istotne. Podczas odtwarzania kodowanego testu interfejsu użytkownika będzie czekać w określonym czasie `(TimeSpan)` przed wstrzymaniem audio. Jeśli przez niektóre specjalne okoliczności upływie określonego czasu przed szukaniem polecenia Wstrzymaj, zostanie wygenerowany wyjątek.


###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Formant wideo
 **Formant wideo:** poprawnie zarejestrowana i odtwarzania akcji w formancie wideo HTML5.

 ![Formant wideo HTML5](../test/media/codedui_html5_video.png)

|Akcja|Rejestrowanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Odtwarzanie wideo**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Odtwórz \<name > wideo z 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Wyszukiwanie się w określonym czasie w wideo**|Wyszukiwanie \<name > film, aby 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Wstrzymaj \<name > wideo na 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Wyciszenia wideo**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Wyciszenia \<name > wideo|HtmlVideo.Mute()|
|**Włącz wideo**<br /><br /> Bezpośrednio z kontroli lub menu kontekstowe kontrolki.|Włącz \<name > wideo|HtmlVideo.Unmute()|
|**Zmień wielkość wideo**|Ustaw wielkość \<name > wideo do 79%||

 Wszystkie właściwości HtmlAudio są dostępne dla HtmlVideo. Ponadto następujące trzy właściwości są również dostępne. Na wszystkich z nich można dodać potwierdzenia.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Wyszukiwanie właściwości:** właściwości wyszukiwania `HtmlVideo` są `Id`, `Name` i `Title`.

 **Właściwości filtru:** właściwości filtru `HtmlVideo` są `Src`, `Poster`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Jeśli rewind lub szybkie przewijanie do przodu wideo przy użyciu-30s lub +30s etykiet, to zostaną zagregowane się w odpowiednim czasie.


###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Suwak
 **Kontrolka suwaka:** poprawnie zarejestrowana i odtwarzania akcji na suwaku HTML5.

 ![HTML5 suwaka](../test/media/codedui_html5_slider.png)

|Akcja|Rejestrowanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Ustaw położenie w suwaka**|Ustaw położenie \<x > w \<name > suwaka|HtmlSlider.ValueAsNumber=\<x>|

 Następujące właściwości są dostępne dla HtmlSlider i na wszystkich z nich można dodać potwierdzenia:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> ProgressBar
 **Formant ProgreesBar:** ProgressBar jest-interactable kontroli. Można dodać asercje `Value` i `Max` właściwościami tego formantu.

 ![HTML5 ProgressBar — formant](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Zobacz także

- [Elementy HTML](http://go.microsoft.com/fwlink/?LinkID=232441)
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
