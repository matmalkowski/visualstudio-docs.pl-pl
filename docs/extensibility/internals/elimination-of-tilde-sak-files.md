---
title: Eliminacja ~ pliki SAK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61227652bf191280f69466f127c4a400ea43856e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="elimination-of-sak-files"></a>Eliminacja ~ SAK plików
W 1.2 interfejsu API dodatku typu Plug-in kontroli źródła ~ SAK pliki zostały zastąpione przez flagi możliwości i nowe funkcje, które wykrywa, czy wtyczka do kontroli źródła obsługuje MSSCCPRJ plików i udostępnionych wyewidencjonowania.  
  
## <a name="sak-files"></a>~ SAK plików  
 Program Visual Studio .NET 2003 utworzone pliki tymczasowe prefiksem ~ SAK. Te pliki służą do określenia, czy obsługuje wtyczka do kontroli źródła:  
  
-   MSSCCPRJ. Plik SCC.  
  
-   Wiele wyewidencjonowania (udostępnionego).  
  
 Dla wtyczki, które obsługuje zaawansowane funkcje oferowane w 1.2 interfejsu API dodatku typu Plug-in kontroli źródła IDE wykrywa te możliwości bez tworzenia plików tymczasowych przy użyciu nowych funkcji, flag i funkcje szczegółowo opisane w poniższych sekcjach.  
  
## <a name="new-capability-flags"></a>Nowe możliwości flagi  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Jeśli wtyczka do kontroli źródła obsługuje wiele wyewidencjonowania (udostępnione), a następnie deklaruje `SCC_CAP_MULTICHECKOUT` możliwości i implementuje `SccIsMultiCheckOutEnabled` funkcji. Ta funkcja jest wywoływana, gdy operacja wyewidencjonowania występuje na żadnym z projektów pod kontrolą źródła.  
  
 Jeśli wtyczka do kontroli źródła obsługuje tworzenie i używanie MSSCCPRJ. Deklaruje SCC plik, a następnie go `SCC_CAP_SCCFILE` możliwości i implementuje [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Ta funkcja jest wywoływana z listą plików. Funkcja zwraca `TRUE/FALSE` dla każdego pliku wskazać, czy program Visual Studio należy używać MSSCCPRJ. Plik SCC dla niego. Jeśli wtyczka do kontroli źródła nie obsługują te nowe możliwości i funkcji, można użyć do wyłączenia tworzenia tych plików następujący klucz rejestru:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
>  Jeśli ten klucz rejestru jest ustawiona na DWORD: 00000000, jest odpowiednikiem klucza jest nieistniejącą i Visual Studio nadal podejmuje próbę utworzenia plików tymczasowych. Jednak jeśli klucz rejestru DWORD: 00000001 Visual Studio nie próbował utworzyć plików tymczasowych. Zamiast tego przyjęto założenie, że wtyczka do kontroli źródła nie obsługuje MSSCCPRJ. Plik SCC i nie obsługuje współdzielonymi wyewidencjonowaniami.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)