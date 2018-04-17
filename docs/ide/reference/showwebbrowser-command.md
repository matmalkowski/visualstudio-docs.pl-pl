---
title: Showwebbrowser — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f699623d15a400b58b3b546a7eb93300385903a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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