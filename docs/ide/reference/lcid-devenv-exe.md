---
title: — Identyfikator LCID (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0588152e99fd6e81d47df691b4e84535cc7fbe9e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Określa domyślny język używany do tekstu, waluty i inne wartości w ramach zintegrowane środowisko programistyczne (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Argumenty  
 `LocaleID`  
 Wymagany. Identyfikator LCID (identyfikator ustawień regionalnych) wybranego języka.  
  
## <a name="remarks"></a>Uwagi  
 Ładuje IDE i ustawia domyślne języka naturalnego dla środowiska. Ta zmiana jest zachowywane między sesjami i odzwierciedlone na **ustawienia międzynarodowe** okienku **środowiska** opcje w **opcje** okno dialogowe w IDE.  
  
 Jeśli określony język nie jest dostępna w systemie użytkownika, przełącznik/LCID jest ignorowany.  
  
 W poniższej tabeli wymieniono LCID języków obsługiwanych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Język|LCID|  
|--------------|----------|  
|Chiński uproszczony|2052|  
|Chiński (tradycyjny)|1028|  
|Angielski|1033|  
|Francuski|1036|  
|niemiecki|1031|  
|Włoski|1040|  
|japoński|1041|  
|koreański|1042|  
|Hiszpański|3082|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie ładuje IDE z ciągów zasobów w języku angielskim.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Ustawienia międzynarodowe, środowisko, opcje — Okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)