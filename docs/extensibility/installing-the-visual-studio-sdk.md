---
title: Instalowanie programu Visual Studio SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/12/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc2d0accfdae3587d43727ec1e0eda0785510c85
ms.sourcegitcommit: 0853338831925fc63398b49f21f457b39f3c0a12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39030432"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalowanie programu Visual Studio SDK

Visual Studio SDK (Software Development Kit) jest opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie zestawu SDK programu Visual Studio w ramach instalacji programu Visual Studio

Aby dołączyć zestawu SDK dla instalacji programu Visual Studio, zainstaluj **programowanie rozszerzeń programu Visual Studio** obciążenie **inne zestawy narzędzi**. To obciążenie zostanie zainstalowany, zestawu SDK programu Visual Studio i niezbędnych wymagań wstępnych. Instalacja jest dalsze dostosowywanie przez zaznaczenie lub usunięcie zaznaczenia składników z **Podsumowanie** widoku.
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie zestawu SDK programu Visual Studio po zainstalowaniu programu Visual Studio

Aby zainstalować zestawu SDK programu Visual Studio po zakończeniu instalacji programu Visual Studio, ponownie uruchom Instalatora programu Visual Studio, a następnie wybierz **programowanie rozszerzeń programu Visual Studio** obciążenia.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalowanie zestawu SDK programu Visual Studio za pomocą rozwiązania

Po otwarciu rozwiązania z projektem rozszerzalności bez instalowania najpierw oprogramowania zestawu SDK dla programu, zostanie wyświetlony monit **instalowanie brakujących funkcji** okno dialogowe, aby zainstalować **programowanie rozszerzeń programu Visual Studio** Obciążenie:

![Zainstaluj rozszerzenie rozwoju](../extensibility/media/install-extension-development.png "zainstalować programowania rozszerzeń")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie zestawu SDK programu Visual Studio z poziomu wiersza polecenia

Za pomocą programu Visual Studio obciążenia lub składnika, można również zainstalować **programowanie rozszerzeń programu Visual Studio** obciążenia (identyfikator: Microsoft.VisualStudio.Workload.VisualStudioExtension) z wiersza polecenia. Zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) szczegółowe informacje dotyczące przełączników wiersza polecenia i ogólne instrukcje na temat określania identyfikatorów obciążenia lub składnika.
  
Należy pamiętać, że należy użyć Instalatora programu Visual Studio, która jest zgodna z zainstalowaną wersją programu Visual Studio. Na przykład w przypadku programu Visual Studio Enterprise zainstalowana na danym komputerze należy uruchomić Instalatora programu Visual Studio Enterprise (vs_enterprise.exe).