---
title: Eliminacja ~ SAK plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a11ed0972c403c4c3ea2a8b3f607135f12e9e315
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677170"
---
# <a name="elimination-of-sak-files"></a>Eliminacja plików ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [eliminacja ~ SAK pliki](https://docs.microsoft.com/visualstudio/extensibility/internals/elimination-of-tilde-sak-files).  
  
W 1.2 interfejsu API wtyczki kontroli źródła ~ SAK pliki zostały zastąpione przez flagi funkcji i nowych funkcji, które wykrywa, czy wtyczka do kontroli źródła obsługuje plików MSSCCPRJ i współdzielonymi wyewidencjonowaniami.  
  
## <a name="sak-files"></a>~ Plików SAK  
 Visual Studio .NET 2003 utworzone pliki tymczasowe z prefiksem ~ SAK. Te pliki są używane do określenia, czy obsługuje wtyczki kontroli źródła:  
  
-   MSSCCPRJ. Plik SCC.  
  
-   Wiele operacji wyewidencjonowania (współużytkowane).  
  
 Wtyczek, które obsługują zaawansowane funkcje udostępniane w 1.2 interfejsu API wtyczki kontroli źródła IDE może wykryć tych funkcji bez tworzenia plików tymczasowych za pomocą nowych możliwości, flag i funkcje, szczegółowo opisane w poniższych sekcjach.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Jeśli wtyczka do kontroli źródła, obsługuje wielu wyewidencjonowania (współużytkowane), a następnie deklaruje `SCC_CAP_MULTICHECKOUT` możliwości i implementuje `SccIsMultiCheckOutEnabled` funkcji. Ta funkcja jest wywoływana zawsze wtedy, gdy operacja wyewidencjonowania odbywa się na żaden z projektów pod kontrolą źródła.  
  
 Jeśli wtyczka do kontroli źródła obsługuje stworzeniem i używaniem MSSCCPRJ. Deklaruje SCC pliku, a następnie ją `SCC_CAP_SCCFILE` możliwości i implementuje [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Ta funkcja jest wywoływana z listą plików. Funkcja zwraca `TRUE/FALSE` dla każdego pliku wskazać, czy program Visual Studio należy używać MSSCCPRJ. Plik SCC dla niego. Jeśli wtyczka do kontroli źródła nie zdecyduje się na obsługuje te nowe możliwości i funkcje, on używać następujący klucz rejestru, aby wyłączyć tworzenie tych plików:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
>  Jeśli ten klucz rejestru DWORD: 00000000 odpowiada kluczowi trwa nieistniejącej i programu Visual Studio nadal podejmuje próbę utworzenia plików tymczasowych. Jednakże jeśli klucz rejestru DWORD: 00000001 programu Visual Studio nie próbuje utworzyć pliki tymczasowe. Zamiast tego przyjęto założenie, że wtyczka do kontroli źródła nie obsługuje MSSCCPRJ. Plik SCC i nie obsługuje współdzielonymi wyewidencjonowaniami.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

