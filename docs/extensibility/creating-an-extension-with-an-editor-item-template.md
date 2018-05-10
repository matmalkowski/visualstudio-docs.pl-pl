---
title: Tworzenie rozszerzenia z szablonem elementu Edytor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fd58c1ada38f8d79402bb08564bf91de23fb086
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia z szablonem elementu edytora
Można użyć szablonów elementów, które znajdują się w Visual Studio SDK do tworzenia podstawowego edytora rozszerzeń, które dodać klasyfikatory, skojarzenia i marginesów do edytora. Szablony elementów edytora są dostępne dla projektów Visual C# lub Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Tworzenie rozszerzenia klasyfikatora  
 Szablon elementu klasyfikatora Edytor tworzy Edytor klasyfikatora, który kolory odpowiedni tekst (w tym przypadku wszystko) w żadnym pliku tekstowego.  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** , a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projektu VSIX**. W **nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **klasyfikatora edytor**. Pozostaw domyślną nazwę pliku (EditorClassifier1.cs).  
  
3.  Istnieją trzy pliki kodu, w następujący sposób:  
  
    -   Zawiera EditorClassifier1.cs `EditorClassifier1` klasy.  
  
    -   Zawiera EditorClassifier1ClassificationDefinition.cs `EditorClassifier1ClassificationDefinition` klasy.  
  
    -   Zawiera EditorClassifier1Format.cs `EditorClassifier1Format` klasy.  
  
    -   Zawiera EditorClassifier1Provider.cs `EditorClassifier1Provider` klasy.  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.  
  
     Po otwarciu pliku tekstowego cały tekst jest podkreślone na tle uzyskania.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Tworzenie rozszerzenia ozdób względem tekstu  
 Szablon edytora tekstu ozdób tworzy ozdób względem tekstu, który decorates wszystkie wystąpienia tekstu znaku "" przy użyciu pola czerwonego obramowania i tło niebieski. Jest tekst względem ponieważ pole zawsze nakładki '' znaków, nawet wtedy, gdy są one przenoszone lub ponownie sformatowany.  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** , a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projektu VSIX**. W **nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **Edytor tekstu ozdób**. Pozostaw domyślną nazwę pliku (TextAdornment1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera TextAdornment1.cs `TextAdornment1` klasy.  
  
    -   Zawiera TextAdornment1TextViewCreationListener.cs `TextAdornment1TextViewCreationListener` klasy.  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. Po otwarciu pliku tekstowego "" znaków w tekście są opisane w czerwony, niebieski tle.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Tworzenie rozszerzenia ozdób względem okienka ekranu  
 Szablon edytora okienka ekranu ozdób tworzy ozdób względem okienka ekranu, który dodaje uzyskania pole, które ma czerwonego obramowania w prawym górnym rogu okienka ekranu.  
  
> [!NOTE]
>  *Okienka ekranu* jest obszar widoku tekstu, który jest aktualnie wyświetlany.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenia ozdób okienka ekranu przy użyciu szablonu ozdób okienka ekranu edytora  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** , a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projektu VSIX**. W **nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **ozdób okienka ekranu edytor**. Pozostaw domyślną nazwę pliku (ViewportAdornment1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera ViewportAdornment1.cs `ViewportAdornment1` klasy.  
  
    -   Zawiera ViewportAdornment1TextViewCreationListener.cs `ViewportAdornment1TextViewCreationListener` — klasa  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. W przypadku utworzenia nowego pliku tekstowego, okno uzyskania, które ma czerwonego obramowania jest wyświetlany w prawym górnym rogu okienka ekranu.  
  
## <a name="creating-a-margin-extension"></a>Tworzenie rozszerzenia margines  
 Szablon marginesu edytora tworzy zielony margines, który pojawi się wraz z wyrazy "Hello world!" poniżej poziomy pasek przewijania.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenia margines przy użyciu szablonu marginesu edytora  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** , a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projektu VSIX**. W **nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **marginesu edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera EditorMargin1.cs `EditorMargin1` klasy.  
  
    -   Zawiera EditorMargin1Factory.cs `EditorMargin1Factory` klasy.  
  
4.  Tworzenie tego projektu i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. Po otwarciu pliku tekstowego zielony margines, który zawiera wyrazy "Hello EditorMargin1" jest wyświetlony poniżej poziomy pasek przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)