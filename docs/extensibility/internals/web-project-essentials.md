---
title: "Podstawowe informacje dotyczące projektu w sieci Web | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ac781256ee78becf3b0cfdffbbec6f0c6bc30225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="web-project-essentials"></a>Podstawowe informacje dotyczące projektu sieci Web
Projekty sieci Web tworzenie aplikacji sieci Web. Projekt sieci Web można użyć do utworzenia aplikacji sieci Web, która ma inteligentne strony sieci Web. Inteligentne strony sieci Web zawiera kod po stronie serwera, który renderuje stronę sieci Web na żądanie.  
  
 Przy użyciu tradycyjnych języków programowania, takich jak [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], można utworzyć inteligentne stron sieci Web do zbierania i przetwarzają informacje od użytkownika, zapisz go w bazie danych i tak dalej.  
  
-   Model kodu powiązanego kojarzy plików kodu źródłowego zależnych ze stronami sieci Web, którzy .aspx rozszerzenia pliku lub .asmx. Na przykład hello.aspx może mieć hello.aspx.cs pliku kodu źródłowego zależnych.  
  
-   Kod po stronie serwera, skojarzony z inteligentne strony sieci Web jest kompilowany do pliku wykonywalnego, który znajduje się w katalogu/bin witryny sieci Web.  
  
-   Pliki kodu źródłowego dodatkowych, takich jak klasy pomocnicze, które nie są skojarzone z określonej strony sieci Web znajdują się w folderze /App_Code witryny sieci Web.  
  
    -   Projekt witryny sieci Web (WSP) generuje jednego pliku wykonywalnego dla każdej inteligentne strony sieci Web. Dodatkowe pliki wykonywalne zostaną wygenerowane na podstawie żadnych plików kodu źródłowego w folderze /App_Code.  
  
    -   Projekt aplikacji sieci Web (WAP) tworzy pojedynczy plik wykonywalny, który łączy kod dla wszystkich stron sieci Web inteligentne, a także wszystkich plików źródłowych w folderze /App_Code.  
  
-   Plik rozwiązania dla projektu sieci Web znajduje się niezależnie od w witrynie sieci Web. Domyślnie pliki rozwiązania znajdują się w \Documents and Settings\\*YourAccount*\My dokumenty\\*\<programu Visual Studio ### >*\Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Jeśli chcesz zachować plik rozwiązania z witryny sieci Web, wystarczy przenieść istnieje i otwórz go ponownie.  
  
-   Po otwarciu witryny sieci Web, która nie ma rozwiązania pliku w Visual Studio nowy plik rozwiązania jest generowane automatycznie dla niego.  
  
-   Projekty sieci Web nie powinny zawierać projektu plików. Informacje o projekcie są przechowywane w pliku rozwiązania, w pliku web.config i w innych miejscach.  
  
-   Dodawanie właściwości globalne do projektu sieci Web automatycznie tworzy plik magazynu w folderze rozwiązania projektu sieci Web.  
  
-   Inteligentne strony sieci Web może być skojarzony z językiem programowania po stronie serwera za pomocą dyrektywy strony lub \<skryptu runat = "server" > tagu.  
  
-   Ponadto stron sieci Web może mieć dowolną liczbę bloków skryptów po stronie klienta w dowolnym języku skryptów.  
  
-   System projektu witryny sieci Web jest implementowany przez dodanie szablonów projektów i elementów i rejestracji w celu [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projektu.  
  
-   WAP system jest implementowany jako podtypu projektu, nazywany również podtypem projektu. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projektu jest języka przez podtyp WAP tworzenia systemu WAP. Aby uzyskać więcej informacji na podtypów projektu, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
-   Inteligentne strony sieci Web łączy HTML z językiem programowania po stronie serwera. Język po stronie serwera jest nazywany zawartych w niej języka. Do obsługi language zawartych w niej, system projektu sieci Web musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodziny interfejsów.  
  
    -   Do obsługi language zawarte w edytorze, usługa języka HTML musi odroczyć wyświetlanie kod języka zawartych w niej do usługi języka zawartych w niej.  
  
    -   Błąd znaczników (czerwony squigglies) zawsze należy utworzyć w buforze podstawowego edytora kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)