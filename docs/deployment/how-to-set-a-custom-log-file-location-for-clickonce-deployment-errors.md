---
title: 'Porady: Ustawianie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a54946f5750e901c937dd91772eb7d7ecb740e48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Porady: ustawienie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Te dzienniki dokumentu błędy dotyczące instalowania i Inicjowanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzą jeden plik dziennika dla każdego wdrożenia aktywacji. Te pliki dziennika są przechowywane w folderze tymczasowych plików internetowych. Plik dziennika dla wdrożenia jest wyświetlane użytkownikowi, gdy wystąpi błąd aktywacji, a użytkownik kliknie **szczegóły** w oknie dialogowym błędu wynikowy.  
  
 To zachowanie można zmienić dla określonego klienta za pomocą Edytora rejestru (**regedit.exe**) można ustawić ścieżkę do pliku dziennika niestandardowego. W takim przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dzienniki aktywacji sukcesy i niepowodzenia we wszystkich wdrożeniach w jednym pliku.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
> [!NOTE]
>  Konieczne będzie obcięcia lub usunąć plik dziennika co pewien czas, aby zapobiec jego zbyt duże.  
  
 W poniższej procedurze opisano sposób ustawiania niestandardowej lokalizacji pliku dziennika dla jednego klienta.  
  
### <a name="to-set-a-custom-log-file-location"></a>Aby ustawić niestandardowej lokalizacji pliku dziennika  
  
1.  Otwórz **Regedit.exe**.  
  
2.  Przejdź do węzła `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Ustaw wartość ciągu `LogFilePath` na pełną ścieżkę i nazwę lokalizacji preferowanych dziennik niestandardowy.  
  
     Lokalizacja musi być w katalogu, do którego użytkownik ma dostęp do zapisu. Na przykład w systemie Windows Vista, utwórz następującą strukturę folderów i ustaw `LogFilePath` do C:\Users\\< nazwa_użytkownika\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)