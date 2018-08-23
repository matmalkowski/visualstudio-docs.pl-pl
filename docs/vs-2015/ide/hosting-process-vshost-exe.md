---
title: Proces hostingu (vshost.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a90a4cd7b829c63070750c34a0cf975f4adea899
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681606"
---
# <a name="hosting-process-vshostexe"></a>Proces hostingu (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [proces hostingu (vshost.exe)](https://docs.microsoft.com/visualstudio/ide/hosting-process-vshost-exe).  
  
Proces hostingu to funkcja w programie Visual Studio, który poprawia wydajność debugowania, włącza debugowanie częściowej relacji zaufania i umożliwia obliczenie wyrażenia czasu projektowania. Pliki procesu hostingu zawierać vshost w nazwie pliku i są umieszczane w folderze danych wyjściowych projektu. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Pliki procesu hostingu (. vshost.exe) są przeznaczone do użytku przez program Visual Studio i nie należy uruchamiać bezpośrednio lub wdrożony z aplikacją.  
  
## <a name="improved-debugging-performance"></a>Zwiększona wydajność debugowania  
 Proces hostingu tworzy domenę aplikacji i kojarzy debugera z aplikacją. Wykonywania tych zadań mogą wprowadzać zauważalnego opóźnienia między debugowanie w czasie została uruchomiona i czas aplikacja rozpoczyna wykonywanie. Proces hostingu pomaga zwiększyć wydajność tworzenia domeny aplikacji i kojarzenie debugera w tle i zapisując domeny aplikacji i stan debugera między uruchomieniami aplikacji. Aby uzyskać więcej informacji na temat domen aplikacji, zobacz [domen aplikacji](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Debugowanie w częściowej relacji zaufania  
 Aplikacja może być określony jako częściowo zaufanych aplikacji w [strony zabezpieczeń](../ide/reference/security-page-project-designer.md) z **projektanta projektu**. Debugowanie aplikacji częściowej relacji zaufania wymaga specjalnych inicjowania domeny aplikacji. Ten proces inicjowania jest obsługiwany przez proces hostingu.  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Obliczanie wyrażenia czasu projektowania umożliwia testowanie kodu z **bezpośrednie** okna bez konieczności uruchamiania aplikacji. Ten kod jest wykonywany w procesu hostingu podczas oceny wyrażenia czasu projektowania. Aby uzyskać więcej informacji, zobacz [bezpośrednim](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
 [Porady: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Domeny aplikacji](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)



