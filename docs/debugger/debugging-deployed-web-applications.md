---
title: Debugowanie aplikacji ASP.NET wdrożonej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/30/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 036b5b5df360631ad10deaff7f63b51cf55cbd3a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-deployed-aspnet-applications"></a>Debugowanie ASP.NET wdrożonej aplikacji
Aby użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania wdrożonych aplikacji, należy dołączyć do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego przetwarzania i upewnij się, że debuger ma dostęp do symboli dla aplikacji. Należy również zlokalizuj i Otwórz pliki źródłowe dla aplikacji. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [porady: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), i [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> Po dołączeniu do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego do debugowania i trafień punktu przerwania, wszystkie zarządzane kodu w zatrzymanie procesu roboczego. Zatrzymywanie zarządzanego kodu w procesie roboczym może spowodować przerwy w pracy dla wszystkich użytkowników na serwerze. Przed debugowania na serwerze produkcyjnym, należy wziąć pod uwagę potencjalnego wpływu na pracę w środowisku produkcyjnym. 
  
Dołączanie do procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy jest taka sama jak dołączanie do zdalnego procesu. Gdy użytkownik jest podłączony, jeśli nie masz poprawny projekt jest otwarty, zostanie wyświetlone okno dialogowe, gdy dzieli aplikację. To okno dialogowe pyta o lokalizacji plików źródłowych dla aplikacji. Nazwa pliku określona w oknie dialogowym musi odpowiadać nazwie określonej w symbole debugowania na serwerze sieci Web. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Aby skonfigurować zdalne debugowanie w usługach IIS, zobacz [zdalnego debugowania ASP.NET na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  Wiele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bibliotek DLL, które zawierają logiki biznesowej lub inny kod przydatne odwołania aplikacji sieci Web. Odniesienie kopiuje biblioteki DLL z komputera lokalnego, w folderze \bin aplikacji sieci Web katalogu wirtualnego, podczas wdrażania aplikacji. Podczas debugowania, należy pamiętać, że aplikacja sieci Web odwołuje się do tej kopii biblioteki dll, a nie kopię na komputerze lokalnym. 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Porady: Włączanie debugowania dla aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Porady: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)