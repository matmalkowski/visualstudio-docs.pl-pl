---
title: Informacje o parametrach w Service1 języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132766"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starsza wersja usługi języka
Etykietka narzędzia informacje o parametrach IntelliSense zapewnia użytkownikom wskazówek, o których są one w konstrukcji języka.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="how-parameter-info-tooltips-work"></a>Jak działają podpowiedź parametru  
 Po wpisaniu instrukcji w edytorze pakiet VSPackage Wyświetla okna małych tooltip z definicją instrukcji jest wpisany. Na przykład wpisz instrukcję Microsoft Foundation Classes (MFC) (takich jak `pMainFrame ->UpdateWindow`) i naciśnij klawisz nawias otwierający, aby rozpocząć, lista parametrów, porada metody zostanie wyświetlone definicji `UpdateWindow` metody.  
  
 Parametr podpowiedź są zazwyczaj używane w połączeniu z uzupełniania instrukcji. Są one najbardziej użyteczne w przypadku języków, które mają parametry lub inne informacje sformatowany po nazwę metody lub słowo kluczowe.  
  
 Informacje o parametrach etykietki narzędzi są inicjowane przez usługę języka za pomocą polecenia zatrzymania. Przechwycenia znaków użytkownika, musi implementować obiekt usługi języka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, a następnie przekaż widoku tekstu wskaźnik do Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu. Filtr polecenia przechwytuje poleceń, które można wpisać w oknie kodu. Monitorowanie informacji o poleceniu wiedzieć, kiedy należy wyświetlić informacje o parametrach dla użytkownika. Ten sam filtr polecenie służy do uzupełniania instrukcji, znaczniki błędów i tak dalej.  
  
 Po wpisaniu słowem kluczowym, dla którego usługa języka zapewniają wskazówki dotyczące usługi języka utworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> obiektu i wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu powiadomiono IDE, aby wyświetlić wskazówki. Utwórz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> przy użyciu `VSLocalCreateInstance` i określając klasy coclass `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` jest funkcją zdefiniowaną w vsdoc.h pliku nagłówka, który wywołuje `QueryService` lokalnego rejestru i wywołania `CreateInstance` w tym obiekcie dla `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Udostępnia wskazówkę — metoda  
 Zapewnienie Porada metody należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfejsu, przekazanie jej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu.  
  
 Jeśli Twoje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> wywołaniu klasy, metody są wywoływane w następującej kolejności:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Zwraca bieżący bufor tekstowy pozycji i długości odpowiednich danych. Powoduje to, że IDE nie mogą zasłaniać danych z okna etykietki narzędzia.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Zwraca liczbę — metoda (liczony od zera indeks) mają być wyświetlane początkowo. Na przykład jeśli zwróci wartość zero, następnie pierwszy przeciążonej metody początkowo jest widoczne.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Zwraca liczbę przeciążonych metod, które mają zastosowanie w bieżącym kontekście. Jeśli zwróci wartość większą niż 1 dla tej metody, następnie widoku tekstu Wyświetla strzałki w górę i w dół za Ciebie. Jeśli kliknij strzałkę w dół, wywołuje metodę IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metody. Jeśli klikniesz przycisk strzałki w górę, wywołuje metodę IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Tekst etykietki narzędzia informacje o parametrach jest tworzony podczas wywołania kilka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Zwraca liczbę parametrów do wyświetlenia w metodzie.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Jeśli metoda liczbę odpowiadającą z przeciążeń, które mają być wyświetlane, ta metoda jest wywoływana, następuje wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informuje o usłudze języka Aby zaktualizować edytor, gdy jest wyświetlany w etykietce — metoda. W <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody, wywołaj następujące:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Pojawi się wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody po zamknięciu okna Porada — metoda.