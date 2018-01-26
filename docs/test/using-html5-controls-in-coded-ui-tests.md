---
title: "Korzystanie z kontrolek HTML5 w kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 093457cf2aea3951db89e6fa677ec03fe55df89a
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika
Kodowane testy interfejsu użytkownika obejmuje obsługę, niektóre z formantów HTML5, które są dołączone do programu Internet Explorer 9 i programu Internet Explorer 10.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  W wersjach wcześniejszych niż program Internet Explorer 10 było możliwe do uruchomienia kodowanych testów interfejsu użytkownika w porównaniu do programu Internet Explorer wyższym poziomie uprawnień. Podczas uruchamiania kodowane testy interfejsu użytkownika w programie Internet Explorer 10, zarówno kodowanego testu interfejsu użytkownika, jak i programu Internet Explorer musi być na tym samym poziomie uprawnień. Jest to spowodowane bardziej bezpieczne funkcje kontenera aplikacji w programie Internet Explorer 10.  
  
> [!WARNING]
>  Jeśli tworzysz kodowanego testu interfejsu użytkownika w programie Internet Explorer 10, może nie zostać uruchomiony przy użyciu programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane programu Internet Explorer 10 zawiera formanty HTML5, takie jak Audio i wideo, ProgressBar oraz Slider. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.  
  
## <a name="supported-html5-controls"></a>Formanty obsługiwanych języków HTML5.  
 Kodowane testy interfejsu użytkownika obejmują obsługę rekordu, odtwarzania i sprawdzania poprawności następujących formantów HTML5:  
  
-   [Audio Control](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Formant wideo](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Slider](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Audio Control  
 **Formant audio:** poprawnie zarejestrowana i odtwarzania akcji w formancie HTML5 Audio.  
  
 ![Formant HTML5 Audio](../test/media/codedui_html5_audio.png "CodedUI_HTML5_Audio")  
  
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
>  Czas wyszukiwania i Wstrzymaj może być istotne. Podczas odtwarzania kodowanego testu interfejsu użytkownika będzie czekać w określonym czasie `(TimeSpan)` przed wstrzymaniem audio. Jeśli przez niektóre specjalne okoliczności upływie określonego czasu przed szukaniem polecenia Wstrzymaj, zostanie wygenerowany wyjątek.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a>Formant wideo  
 **Formant wideo:** poprawnie zarejestrowana i odtwarzania akcji w formancie wideo HTML5.  
  
 ![Formant wideo HTML5](../test/media/codedui_html5_video.png "CodedUI_HTML5_Video")  
  
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
>  Jeśli rewind lub szybkie przewijanie do przodu wideo przy użyciu-30s lub +30s etykiet, to zostaną zagregowane się w odpowiednim czasie.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a>Suwak  
 **Kontrolka suwaka:** poprawnie zarejestrowana i odtwarzania akcji na suwaku HTML5.  
  
 ![Kontrolka suwaka HTML5](../test/media/codedui_html5_slider.png "CodedUI_HTML5_Slider")  
  
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
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a>ProgressBar  
 **Formant ProgreesBar:** ProgressBar jest-interactable kontroli. Można dodać asercje `Value` i `Max` właściwościami tego formantu.  

 ![Formant HTML5 ProgressBar](../test/media/codedui_html5_progressbar.png "CodedUI_HTML5_ProgressBar")  

## <a name="see-also"></a>Zobacz także

[Elementy HTML](http://go.microsoft.com/fwlink/?LinkID=232441)  
[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)  
[Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)  
[Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
