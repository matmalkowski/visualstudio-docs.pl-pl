---
title: "Porady: zapisywanie i otwieranie kodowanych plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13b00135adfe3d65adeed7eecc5f9e22e4b7a2cb
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Porady: zapisywanie i otwieranie kodowanych plików
Pliki można zapisywać znakiem określonego kodowania w celu włączenia obsługi języków dwukierunkowych. Można również określić kodowania podczas otwierania pliku, tak, aby poprawnie Wyświetla plik programu Visual Studio.  
  
### <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem  
  
1.  Z **pliku** menu, wybierz **Zapisz plik jako**, a następnie kliknij przycisk listy rozwijanej obok pola **zapisać** przycisku.  
  
     **Zaawansowane opcje zapisywania** zostanie wyświetlone okno dialogowe.  
  
2.  W obszarze **kodowanie**, wybierz kodowanie do użycia dla pliku.  
  
3.  Opcjonalnie w obszarze **zakończenia wierszy**, wybierz format znaki końca wiersza.  
  
     Ta opcja jest przydatna, jeśli zamierzasz wymiany pliku z użytkowników z poziomu innego systemu operacyjnego.  
  
     Jeśli chcesz pracować z plikiem, który znasz jest zakodowany w określony sposób można stwierdzić, Visual Studio, aby użyć kodowania podczas otwierania pliku. Używanej metody zależy od tego, czy plik jest częścią projektu.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć zakodowany plik, który jest częścią projektu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik i wybierz opcję **Otwórz za pomocą**.  
  
2.  W **Otwórz za pomocą** okno dialogowe, wybierz Otwórz plik w edytorze.  
  
     Wiele edytorów Visual Studio, takich jak edytor formularzy Autowykrywanie kodowania, a następnie otwórz plik odpowiednio. Jeśli wybierzesz edytor, który umożliwia wybranie kodowania, **kodowanie** zostanie wyświetlone okno dialogowe.  
  
3.  W **kodowanie** oknie dialogowym Wybierz kodowanie, które powinny być używane w edytorze.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć zakodowany plik, który nie jest częścią projektu  
  
1.  Na **pliku** menu wskaż **Otwórz**, wybierz **pliku** lub **plik z sieci Web**, a następnie wybierz plik, aby otworzyć.  
  
2.  Kliknij przycisk listy rozwijanej obok pola **Otwórz** przycisk i wybierz polecenie **Otwórz za pomocą**.  
  
3.  Wykonaj kroki 2 i 3 w poprzedniej procedurze.  
  
## <a name="see-also"></a>Zobacz także
[Kodowanie i podziały wierszy](encodings-and-line-breaks.md)  
[Kodowanie i globalizacja formularzy systemu Windows](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)   
[Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)