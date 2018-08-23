---
title: 'Porady: używanie diagnostyki grafiki z urządzeniem ARM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24067412f875001185a0709c41f930ce3cdc8f3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682581"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Porady: używanie diagnostyki grafiki z urządzeniem ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Diagnostyka grafiki z urządzeniem ARM](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-use-graphics-diagnostics-with-an-arm-device).  
  
Graphics Diagnostics obsługuje zdalne debugowanie aplikacji Direct3D na urządzeniach z systemem ARM z systemem Windows RT 8.1 lub Windows Phone 8.1. Możesz przechwytywać informacje graficzne z aplikacji Direct3D, po uruchomieniu na urządzeniu lub korzystanie z urządzenia jako maszynę odtwarzającą dla wcześniej przechwycone informacje graficzne.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Używanie Graphics Diagnostics przy użyciu urządzenia z systemem ARM  
 Ponieważ program Visual Studio nie jest uruchamiany na urządzeniach z systemem ARM, masz umożliwia analizowanie aplikacja, która działa na nich za pomocą zdalnego debugera. Zdalny debuger obsługuje przechwytywanie grafiki i odtwarzanie tak, aby zdiagnozować błędy renderowania i po prostu równie łatwo, jak można debugować aplikację na nich ocenić wydajność grafiki na tych urządzeniach.  
  
 Korzystanie z funkcji diagnostyki grafiki, należy najpierw włączyć, zdalne debugowanie na urządzeniu.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Aby włączyć debugowanie zdalne na urządzeniu z systemem ARM  
  
1.  Zainstaluj [zasad dotyczących zestawów ARM](http://msdn.microsoft.com/windows/desktop/dn469188) na urządzeniu z systemem ARM.  
  
2.  Zainstaluj [Remote Debugging Tools](http://go.microsoft.com/fwlink/?LinkId=393086) na urządzeniu z systemem ARM.  
  
> [!IMPORTANT]
>  Urządzeń z systemem Windows Phone 8.1 trzeba zarejestrować telefon do programowania. Aby to zrobić, musi być zarejestrowany dla deweloperów. Aby uzyskać więcej informacji, zobacz [sposób wdrażania i uruchamiania aplikacji dla systemu Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Po włączeniu zdalnego debugowania na urządzeniu z systemem przekształcić ją w docelowych debugowania i uruchom narzędzie Diagnostyka grafiki.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Aby skonfigurować i uruchomić diagnostyki grafiki na urządzeniu z systemem  
  
1.  Na **platformy rozwiązania** listy rozwijanej wybierz **ARM** tak, aby urządzenia z systemem ARM będą dostępne jako obiekt docelowy debugowania zdalnego.  
  
2.  Na **Debuguj element docelowy** listy rozwijanej wybierz urządzenie ARM.  
  
3.  W menu, wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**. (Klawiatura: Alt + F5)  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Instrukcje: zmiana maszyny odtwarzania diagnostyki grafiki](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



