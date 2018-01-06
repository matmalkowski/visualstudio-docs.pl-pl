---
title: "DA0030: Gromadzenie pomiarów interakcji warstwowej dla projektów bazy danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a41357670b7f9c634de57f66bd292320d354dbc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Gromadzenie pomiarów interakcji warstwowej dla projektów bazy danych
|||  
|-|-|  
|Identyfikator reguły|DA0030|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Pobierania próbek|  
|Komunikat|Zebranie pomiarów interakcji dla aplikacji wielowarstwowych będzie ułatwiające zrozumienie, jakie wzorce wykorzystania bazy danych i danych klucza dostępu opóźnienia. Spróbuj ponownie sprofilować aplikację z włączoną opcją profilowania interakcji między warstwami.|  
|Typ reguły|Informacje|  
  
## <a name="cause"></a>Przyczyna  
 Wywołuje się <xref:System.Data> znaczną ilość danych profilowania są metody i nie zgromadzono danych o interakcji między warstwy w przebiegu profilowania. Należy wziąć pod uwagę profilowanie ponownie i dodaniu interakcji danych.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada wyzwala zawsze, gdy jest istotne działania funkcji, które znajdują się w przestrzeni nazw dane systemowe, w tym <xref:System.Data.Linq> <xref:System.Data.Linq>.  
  
 Aplikacji wielowarstwowych za pomocą warstw usług ich warstwy prezentacji i danych. Warstwa danych jest często osobnych procesach systemu zarządzania bazy danych, takich jak Microsoft Sql Server. Warstwa danych może być uruchomiona nawet na osobnym komputerze od pozostałej części aplikacji. Profile próbkowania zapewniają małego wgląd w funkcji i usług działających poza procesem lub zdalnie.  
  
 Narzędzia profilowania umożliwia zebranie informacji chronometrażu dla aplikacji wielowarstwowych, które pracują z warstwy danych programu Microsoft Sql Server przy użyciu wywołania asynchroniczne do usług ADO.NET. Musisz jawnie włączyć profilowanie interakcji między warstwami. Go nie jest włączona domyślnie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ta zasada jest wyłącznie do celów informacyjnych i nie może wymagać działań korygujących.  
  
 Aby uzyskać informacje dotyczące sposobu dodawania danych o interakcji między warstwy do profilowania danych z programu Visual Studio IDE, zobacz [zbierania danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md). Aby uzyskać informacje dotyczące sposobu dodawania danych interakcji z wiersza polecenia, zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).