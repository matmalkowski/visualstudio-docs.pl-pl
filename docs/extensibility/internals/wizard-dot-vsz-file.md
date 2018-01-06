---
title: Kreator (. Pliku Vsz) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f70d41b353640a3b2b108a55f14b8737a7fe1f8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-vsz-file"></a>Kreator (. Pliku Vsz)
Zintegrowane środowisko programistyczne (IDE) używa plików .vsz, aby uruchomić kreatora. Te pliki .vsz zawierają informacje, które IDE używa w celu określenia, które kreatora w celu wywołania i jakie informacje do przekazania do kreatora.  
  
 Plik .vsz jest wersja pliku tekstu w formacie pliku ini, który ma sekcji. Informacje o znanych IDE są przechowywane na początku pliku. Zapewnia to łącze między kreatora, który wywołuje IDE oraz parametry, które znajdują się w pliku .vsz do przekazania do środowiska IDE. Pozostała część pliku zawiera parametry specyficznych dla kreatora i które mają zostać zebrane przez IDE i przekazywane do określonych kreatora.  
  
 W poniższym przykładzie przedstawiono zawartość pliku .vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Poniżej przedstawiono części w pliku .vsz.  
  
|Część|Opis|  
|----------|-----------------|  
|VSWizard|Pierwszy parametr w pliku jest numer wersji formatu pliku szablonu. Ten numer wersji musi być w wersji 6.0, 7.0, 7.1 lub 8.0. Inne liczby nie może zostać uruchomiona i spowodować wystąpienie błędu nieprawidłowy Format.|  
|Kreator|To pole zawiera OLE programu kreatora lub identyfikator GUID reprezentację ciągu identyfikatora CLSID kreatora, który jest cocreated IDE.|  
|Param|Części te są opcjonalne. Można dodać więcej niż wymagana.|  
  
 Parametry włączyć plik .vsz można przekazywać dodatkowych parametrów niestandardowych do kreatora. Każda wartość jest przekazywany jako ciąg element w tablicy typu Variant do kreatora. Aby uzyskać więcej informacji, zobacz [niestandardowe parametry](../../extensibility/internals/custom-parameters.md). Aby uzyskać informacje o sposobie używania pliku .vsz do tworzenia niestandardowych kreatorów, zobacz [. Pliku Vsz (kontrola projektu)](/cpp/ide/dot-vsz-file-project-control)  
  
 Aby dodać plik .vsz domyślny identyfikator ustawień regionalnych, określić `FALLBACK_LCID`= xxxx, gdzie xxxx to identyfikator ustawień regionalnych, na przykład 1033 dla języka angielskiego. Gdy `FALLBACK_LCID` zdefiniowano parametru, jeśli bieżący identyfikator nie zostanie znaleziony, kreator używa Identyfikatora ustawień regionalnych rezerwowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)