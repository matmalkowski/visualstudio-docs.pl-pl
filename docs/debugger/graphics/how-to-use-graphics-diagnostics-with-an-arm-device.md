---
title: "Porady: Użyj diagnostyki grafiki z urządzeniem ARM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60898b7ea37c7e732453fd03f9c557b2494f66c5
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Porady: Użyj diagnostyki grafiki z urządzeniem ARM
Diagnostyka grafiki obsługuje zdalne debugowanie aplikacji Direct3D na urządzeniach z systemem ARM z systemem Windows RT 8.1 lub Windows Phone 8.1. Przechwytywanie informacji graficznych z aplikacji Direct3D ona działać na urządzeniu lub korzystać z urządzenia jako maszynie odtwarzającej grafiki przechwyconych wcześniej informacji.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Urządzenia oparte na usłudze ARM przy użyciu diagnostyki grafiki  
 Ponieważ program Visual Studio nie działa na urządzeniach z systemem ARM, należy użyć zdalnego debugera do analizowania aplikacji, która działa na nich. Zdalny debuger obsługuje przechwytywania grafiki i odtwarzania, dzięki czemu można diagnozowanie błędów renderowania i równie proste, jak można debugować aplikacji na nich ocenić wydajność grafiki na tych urządzeniach.  
  
 Aby używać funkcji diagnostyki grafiki, najpierw włączyć debugowanie zdalne na urządzeniu.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Aby włączyć debugowanie zdalne na urządzeniu z systemem ARM  
  
1.  Zainstaluj [zasad dotyczących zestawów ARM](http://msdn.microsoft.com/windows/desktop/dn469188) na urządzeniu z systemem ARM.  
  
2.  Zainstaluj [narzędzia do zdalnego debugowania](http://go.microsoft.com/fwlink/?LinkId=393086) na urządzeniu z systemem ARM.  
  
> [!IMPORTANT]
>  W przypadku urządzeń Windows Phone 8.1 trzeba będzie zarejestrować telefon do programowania aplikacji. Aby to zrobić, musi być zarejestrowany developer. Aby uzyskać więcej informacji, zobacz [sposób wdrażania i uruchamiania aplikacji dla systemu Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Po włączeniu zdalnego debugowania na twoim urządzeniu była docelowego debugowania i rozpocząć diagnostyki grafiki.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Aby skonfigurować i uruchomić diagnostyki grafiki na urządzeniu  
  
1.  Na **platformy rozwiązania** listy rozwijanej wybierz **ARM** tak, aby urządzenia z systemem ARM będą dostępne jako cel debugowania zdalnego.  
  
2.  Na **docelowego debugowania** listy rozwijanej wybierz urządzenie ARM.  
  
3.  W menu, wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**. (Klawiatury: Alt + F5)  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym](../run-windows-store-apps-on-a-remote-machine.md)   
 [Porady: zmiana maszyny odtwarzania diagnostyki grafiki](how-to-change-the-graphics-diagnostics-playback-machine.md)