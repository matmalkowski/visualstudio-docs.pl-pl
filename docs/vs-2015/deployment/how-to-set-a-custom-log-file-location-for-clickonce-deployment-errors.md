---
title: 'Porady: ustawienie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 9f061037b6349838b145627125527f64b68a2856
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632079"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Porady: ustawienie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Ustaw lokalizację niestandardowego pliku dziennika błędów wdrażania technologii ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Te dzienniki dokumentu wszelkie błędy dotyczące instalowania i Inicjowanie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tworzy jeden plik dziennika dla każdego wdrożenia aktywacji. Przechowuje te pliki dziennika w folderze tymczasowych plików internetowych. Plik dziennika dla wdrożenia jest wyświetlany użytkownikowi, wystąpi błąd aktywacji, gdy użytkownik kliknie **szczegóły** wynikowy w oknie dialogowym błędu.  
  
 To zachowanie można zmienić dla konkretnego klienta, za pomocą Edytora rejestru (**regedit.exe**) można ustawić ścieżki pliku dziennika niestandardowego. W tym przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dzienników aktywacji sukcesów i niepowodzeń dla wszystkich wdrożeń w jednym pliku.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
> [!NOTE]
>  Konieczne będzie obcięcia lub usunąć plik dziennika co pewien czas, aby uniemożliwić zbyt duże.  
  
 Poniższa procedura opisuje sposób ustawiania niestandardowej lokalizacji pliku dziennika dla jednego klienta.  
  
### <a name="to-set-a-custom-log-file-location"></a>Aby ustawić lokalizację pliku dziennika niestandardowego  
  
1.  Otwórz **Regedit.exe**.  
  
2.  Przejdź do węzła `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Ustaw wartość ciągu `LogFilePath` pełną ścieżkę i nazwę pliku dziennika niestandardowego preferowanych lokalizacji.  
  
     Ta lokalizacja musi być w katalogu, do którego użytkownik ma dostęp do zapisu. Na przykład na Windows Vista, utwórz następującą strukturę folderów i ustawić `LogFilePath` do C:\Users\\< nazwa_użytkownika\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)





