---
title: "Wybieranie strategii wdrażania aparat debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d08d82f867ac2723ff68da615d5dc6977b8038af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Wybieranie strategii wdrażania aparat debugowania
Architektura środowiska wykonawczego umożliwia określanie strategii wdrażania (DE) Aparat debugowania. Aparat debugowania może zostać utworzony w trakcie do programu debugowany, proces Menedżera debugowania sesji programu Visual Studio (SDM) lub poza procesem do obu z nich. Poniższe wskazówki powinna ułatwić wybranie jednego z tych trzech strategii.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Gdy istnieje możliwość DE się poza procesem do SDM i programu do debugowania, nie istnieje zwykle Przyczyna Aby to zrobić. Wywołania przez granice procesu są stosunkowo powolne.  
  
 Debugowanie aparaty są już udostępniane dla środowiska Win32 natywnego środowiska wykonawczego i środowisko uruchomieniowe języka wspólnego. Jeśli musisz zastąpić DE dla dowolnego z tych środowisk, należy utworzyć z SDM DE w procesie.  
  
 W przeciwnym razie można wybrać tworzenie DE procesu do SDM lub proces programu do debugowania. Należy wziąć pod uwagę, czy ewaluatora wyrażenia z DE wymaga częste dostępu do magazynu symboli program i czy magazynu symboli mogą być ładowane do pamięci w celu szybkiego dostępu. Również uwzględnić następujące kwestie:  
  
-   Jeśli nie ma wiele wywołań między ewaluatora wyrażenia, a także przechowywać symbolu lub magazynu symboli mogą być odczytywane w obszarze pamięci SDM, Utwórz DE w procesie do SDM. Identyfikator CLSID aparat debugowania musi zwrócić SDM po dołączeniu do programu. SDM używa tego identyfikatora CLSID w celu utworzenia wystąpienia w trakcie DE.  
  
-   Jeśli DE musi wywołać program dostępu do magazynu symboli, Utwórz DE w procesie z programu. W takim przypadku program tworzy wystąpienie DE.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)