---
title: Wybieranie strategii implementacji aparatu debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 058e3d3087a46de4bb3c5d9b721d3c9111b77526
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203715"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Wybieranie strategii implementacji aparatu debugowania
Architektura środowiska wykonawczego umożliwia określenie strategii implementacji aparatu (DE) debugowania. Można utworzyć aparatu w — proces debugowania do programu, który debugujesz. Utwórz debugowania aparatu wewnątrz procesu Menedżer debugowania sesji programu Visual Studio (SDM). Lub Utwórz debugowania aparatu poza procesem do obu z nich. Poniższe wskazówki pomoże wybrać jeden z tych trzech strategii.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Choć jest możliwe do DE to spoza procesu SDM i program debugujesz zwykle nie ma powodu aby to zrobić. Wywołania przez granice procesu są stosunkowo wolno.  
  
 Debugowanie aparaty są już udostępniane dla środowiska wykonawczego natywny Win32 i środowiska uruchomieniowego języka wspólnego. Jeśli musisz zastąpić "de" dla jednego środowiska, należy utworzyć DE w procesie z SDM.  
  
 W przeciwnym razie albo utworzysz DE wewnątrz procesu SDM lub debugujesz procesu do programu. Należy wziąć pod uwagę, jeśli ewaluatora wyrażenia z DE wymaga częstego dostępu do magazynu symboli programu. Lub, jeśli w magazynie symboli może być załadowany do pamięci, aby uzyskać szybki dostęp. Ponadto należy wziąć pod uwagę następujących metod:  
  
-   Jeśli nie ma wiele wywołań między Ewaluator wyrażeń i magazynu symboli lub mogą być odczytywane w magazynie symboli do obszaru pamięci SDM, należy utworzyć DE wewnątrz procesu SDM. Identyfikator CLSID aparat debugowania musi zwrócić SDM, po dołączeniu do programu. SDM używa tego identyfikatora CLSID, do utworzenia wystąpienia w trakcie DE.  
  
-   Jeśli DE musi wywołać program, który ma dostęp do magazynu symboli, należy utworzyć DE w procesie z programem. W takim przypadku program tworzy wystąpienie DE.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)