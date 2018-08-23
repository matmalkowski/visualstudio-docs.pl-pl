---
title: Showwebbrowser — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de730650216f67d3f620fa85cad0a98148ce2ee3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42671041"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [showwebbrowser — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/showwebbrowser-command).  
  
  
Wyświetla adres URL w oknie przeglądarki sieci Web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argumenty  
 `URL`  
 Wymagane. Adres URL (Uniform Resource Locator) dla witryny sieci Web.  
  
## <a name="switches"></a>Przełączniki  
 / Nowy  
 Opcjonalna. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci Web.  
  
 /ext  
 Opcjonalna. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.  
  
## <a name="remarks"></a>Uwagi  
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wyświetla MSDN Online strony głównej w przeglądarce sieci Web poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarty, jest używany; w przeciwnym razie jest uruchamiana nowe wystąpienie.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



