---
title: 'Porady: Zarządzanie plikami danych lokalnych w projekcie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b63a90a354935300c705c0bf96ae307e0468b4f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690152"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Porady: zarządzanie plikami danych lokalnych w projekcie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plik lokalnej bazy danych może być uwzględniany jako plik w projekcie. Przy pierwszym połączeniu z plikiem lokalnej bazy danych, można wybrać tworzenie kopii w projekcie lub Połącz z istniejącego pliku w jego bieżącej lokalizacji. Jeśli łączysz się z istniejącym plikiem, pozostanie w jej oryginalnej lokalizacji. Jeśli chcesz skopiować plik do projektu programu Visual Studio tworzy kopię, dodaje go do projektu i modyfikuje połączenie tak, aby wskazać polecenie kopiowania. Inne połączenia, takich jak te w Eksploratorze serwera również są modyfikowane.  
  
 Ustawienie domyślne właściwości zależy od typu pliku bazy danych, którego używasz. Zachowanie **Kopiuj do katalogu wyjściowego** właściwość nie ma zastosowania do projektów sieci Web lub C++.  
  
 Podczas tworzenia aplikacji możesz chcieć wyświetlić efekty swój kod w bazie danych bez konieczności wprowadzenia tych zmian na stałe. Możesz to zrobić przez ustawienie opcji **Kopiuj do katalogu wyjściowego** własności pliku na wartość true. Każdorazowo kompilacji projektu lub naciśnij klawisz F5, plik jest kopiowany do folderu bin i zmiany zostały wprowadzone do tego pliku, a nie do pliku w folderze głównym projektu. Plik bazy danych w folderze głównym projektu zostanie zmieniony tylko wtedy, gdy edytujesz schemat bazy danych lub dane za pomocą **Eksploratora serwera**, **Eksplorator bazy danych** lub inne okna narzędzi.  
  
 W poniższej tabeli opisano ustawienia **Kopiuj do katalogu wyjściowego** właściwości.  
  
|Ustawienie|Zachowanie|  
|-------------|--------------|  
|**Kopiuj Jeśli nowszy** (wartość domyślna dla plików .sdf)|Plik bazy danych jest kopiowany z katalogu projektu do **bin** czasu katalogu pierwszy projekt jest kompilowany. Każdym późniejszym kompilowaniu projektu **Data modyfikacji** jest porównywana właściwość plików. Jeśli plik w folderze projektu jest nowszy, jest kopiowany do **bin** folderu, zastępując plik, który jest tam aktualnie. Jeśli plik w **bin** folderu jest nowszy, żadne pliki nie są kopiowane. To ustawienie utrzymuje wszelkie zmiany wprowadzone do danych w czasie wykonywania, co oznacza, że za każdym razem, gdy uruchomisz aplikację i Zapisz zmiany w danych, zmiany te są widoczne przy następnym uruchomieniu aplikacji. **Uwaga:** nie zaleca się tej opcji dla plików .mdb lub .mdf. Plik bazy danych można zmienić nawet wtedy, gdy dane są wprowadzane żadne zmiany. Otwieranie połączenia w pliku danych (na przykład poprzez rozwijanie **tabel** w węźle **Eksploratora serwera**) może je oznaczyć jako nowsze.|  
|**Zawsze Kopiuj** (domyślnie dla plików .mdf i .mdb)|Plik bazy danych jest kopiowany z katalogu projektu do katalogu/bin za każdym razem, gdy kompilujesz aplikację. W związku z tym jeśli kompilujesz aplikację i Zapisz zmiany w pliku w katalogu/bin, zmiany te są zastępowane przy następnym uruchomieniu oryginalny plik jest kopiowany do katalogu/bin.|  
|**Nie Kopiuj**|Plik nigdy nie jest kopiowany ani zastąpiona przez system projektu. Możesz musisz ręcznie skopiować plik z katalogu projektu do katalogu wyjściowego Jeśli używasz tego ustawienia.|  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Aby odpowiedzieć na oknie dialogowym pliku lokalnej bazy danych  
  
-   Kliknij przycisk **tak** Jeśli chcesz, aby program Visual Studio skopiował plik bazy danych do projektu i zmodyfikuj połączenie, aby wskazać polecenie kopiowania do projektu. Aby uzyskać więcej informacji na temat pracy z plikami bazy danych w projekcie, zobacz [Local Data Overview](../data-tools/local-data-overview.md).  
  
-   Kliknij przycisk **nie** Jeśli nie chcesz, aby program Visual Studio skopiował plik bazy danych do projektu. Zamiast tego punkty połączeń do pliku w oryginalnej lokalizacji i plik bazy danych nie został dodany jako plik do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Łączenie z danymi w pliku lokalnej bazy danych (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Łączenie z danymi w bazie danych programu Access (formularze Windows)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)