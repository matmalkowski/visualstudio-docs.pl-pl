---
title: "Showwebbrowser — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie
Wyświetla adres URL, określ w oknie przeglądarki sieci Web albo w ramach zintegrowane środowisko programistyczne (IDE) lub zewnętrzne względem programu IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argumenty  
 `URL`  
 Wymagany. Adres URL (Uniform Resource Locator) dla witryny sieci Web.  
  
## <a name="switches"></a>Przełączniki  
 / new  
 Opcjonalny. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci Web.  
  
 /ext  
 Opcjonalny. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.  
  
## <a name="remarks"></a>Uwagi  
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono MSDN Online strony głównej w przeglądarce sieci Web poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarty, jest używany; w przeciwnym razie uruchamiane jest nowe wystąpienie.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)