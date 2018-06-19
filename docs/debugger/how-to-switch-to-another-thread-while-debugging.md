---
title: 'Porady: przełączanie na inny wątek podczas debugowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7e5e3b127dd397a32b54915f95827ebe5649f5f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475689"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Porady: przełączanie na inny wątek podczas debugowania w programie Visual Studio
Podczas debugowania aplikacji wielowątkowych służy jednej z kilku metod przejść z wątku, który pracy z do innego wątku.

> [!NOTE]
> Jeśli chcesz kontrolować kolejność, w którym wykonywanie wątków, musisz [zablokować i odblokować wątków](../debugger/get-started-debugging-multithreaded-apps.md).

Po sprawdzeniu wątków w edytorze kodu i oknach debugowania wielowątkowe żółta strzałka wskazuje bieżący wątek. Zielona strzałka z nawiasy tail oznacza, że wątek długoterminowe ma bieżącego kontekstu debugera.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Aby przełączyć się do dowolnego wątku, który pojawi się 
  
-   W **wątków** lub **czujki równoległej** okna, kliknij dwukrotnie wątek.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródła  
  
-   W odstępu po lewej stronie, kliknij prawym przyciskiem myszy ikonę znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker"), wskaż **przełączyć się do**, a następnie kliknij nazwę tego wątku, do której chcesz przełączyć . Menu skrótów pokazuje wątki w określonej lokalizacji.  
  
     Jeśli zostanie wyświetlony bez znaczników wątku, kliknij prawym przyciskiem myszy w **wątków** okna i sprawdź, czy **Pokaż wątki w źródle** jest zaznaczone.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku w pasku narzędzi debugowania lokalizacji  
  
1.  Na **debugowania lokalizacji** narzędzi, kliknij przycisk **wątku** listy.  
  
2.  Na liście kliknij wątek, do której chcesz przełączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)
