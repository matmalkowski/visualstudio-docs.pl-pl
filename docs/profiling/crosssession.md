---
title: CrossSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 079e0ec1b2bad2ca01a698c474c37de6d5d7dfd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="crosssession"></a>CrossSession
VSPerfCmd.exe **CrossSession** opcja umożliwia profilera do zbierania danych z dowolnej sesji konsoli. **CrossSession** opcji należy używać z **Start** opcji.  
  
 Można używać skrótu **CS** zamiast **CrossSession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Aby włączyć profilowanie w innej sesji **CrossSession** można określić opcji z **Start** opcji. **CrossSession** musi być także określona w żadnym kolejnych **dołączyć VSPerfCmd** i **Detach** poleceń.  
  
 **Start:**`Method`  
 **Start** opcji inicjowania profilera do określonej metody profilowania.  
  
 **Dołącz:** *PID*[**,***PID*]  
 Rozpoczyna się profilowania określonych procesów.  
  
 **Odłącz**[**:***PID*[,*PID*]]  
 Zatrzymuje profilowanie określonych procesów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **CrossSession** jest używana opcja Dołącz do aplikacji, które zostało uruchomione w innej sesji konsoli.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)