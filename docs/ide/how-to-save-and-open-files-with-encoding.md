---
title: 'Porady: zapisywanie i otwieranie kodowanych plików | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6375852a76da633707c90538945339e438aac4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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