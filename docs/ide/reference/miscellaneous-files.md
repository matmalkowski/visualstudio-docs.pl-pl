---
title: Różne pliki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e020e1cc38898f830537afc2346fd20711cd587
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="miscellaneous-files"></a>Folder różnych plików
Możesz chcieć użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] edytory pracy niezależnie z projektem lub rozwiązaniem. Gdy masz otwartego rozwiązania można otwierać i modyfikować pliki bez dodawania ich do rozwiązania lub projektu. Pliki, które chcesz pracować z niezależnie od kontenery są nazywane różne pliki. Różne pliki są zewnętrzne rozwiązania i projekty nie są uwzględnione w kompilacji i nie może zostać dołączony do rozwiązania pod kontrolą źródła.  
  
 Otwieranie plików niezależnie od kontener jest przydatne w przypadku z różnych przyczyn. Może mieć plik, który chcesz wyświetlić, podczas tworzenia projektu rozwiązania, ale nie jest integralną częścią opracowywanie rozwiązań. Typowe przykłady obejmują uwagi rozwoju lub instrukcji, schemat bazy danych i klipów kodu. Ponadto można utworzyć pliku autonomicznym.  
  
 ![Projekty rozwiązań](../../ide/reference/media/projects_solutions_misc.gif "Projects_Solutions_Misc")  
  
 Eksplorator rozwiązań można wyświetlić folder różnych plików dla plików, gdy są włączone opcje folderu. Można ustawić opcji [dokumenty, środowisko, opcje — Okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md). Po zamknięciu dodatkowych plików nie jest skojarzony z danego rozwiązania lub projektu, chyba że jest włączona opcja w tym również.  
  
 Folder różnych plików reprezentuje pliki jako łącza. Chociaż ten folder nie jest częścią rozwiązania, po otwarciu rozwiązania, niektóre lub wszystkie różne pliki, które zostały otwarte podczas ostatniego zamknięcia rozwiązania są ponownie otworzyć, w zależności od ustawienia dla folderu.  
  
> [!NOTE]
>  Niektóre pliki, które nie są wyświetlane w folderze plików pozostałych są pliki, których nie można zmodyfikować w środowisku IDE, takich jak pliki zip i doc. IDE nie będzie śledzić pliki, które można modyfikować tylko za pomocą zewnętrznego edytora.  
  
## <a name="commands-available-in-the-ide"></a>Polecenia dostępne w środowisku IDE  
 Menu i pasków narzędzi, polecenia, które zawierają zmiany na podstawie formatu pliku możesz otworzyć. Po otwarciu pliku tekstowego, na przykład zostanie wyświetlony pasek narzędzi edytora tekstowego i polecenia są dostępne. Jeśli następnie otwórz plik XML schematu, zostanie wyświetlony pasek narzędzi schematu XML. Podczas edycji schematów XML, paska narzędzi edytora tekstu polecenia (lub na pasku narzędzi, sam) są niedostępne. Schemat XML jest aktywne okno i jako taki, ma bieżący kontekst zaznaczenia. Podczas przełączania między pliku projektu i pliku różne znikają wszystkich poleceń związanych z projektem i są wyświetlane tylko te, które są bezpośrednio związane z dodatkowych plików.  
  
## <a name="folder-display-options"></a>Opcje wyświetlania folderu  
 Można ustawić opcje wyświetlania Folder różnych, dzięki czemu folderu pojawia się, nawet jeśli nie została jeszcze otwarta żadnych dodatkowych plików. Plik rozwiązania nie zarządza trwale lista dodatkowych plików. Opcjonalna funkcja umożliwiająca do zapamiętania dla poszczególnych użytkowników ostatnio używanych (MRU) lista plików jest używany.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Dokumenty, środowisko, opcje — Okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md)