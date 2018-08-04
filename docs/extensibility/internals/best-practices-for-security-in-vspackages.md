---
title: Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5b3b86736a5425640c1a87df6a3e2c6e6cec0c5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513351"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage
Aby zainstalować [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] na komputerze, użytkownik musi być uruchomiona w kontekście przy użyciu poświadczeń administracyjnych. Podstawowa jednostka zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacja jest [pakietu VSPackage](../../extensibility/internals/vspackages.md). Pakietu VSPackage muszą być zarejestrowane przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], które również wymaga poświadczeń administracyjnych.  
  
 Administratorzy mają pełne uprawnienia do zapisu do rejestru i systemu plików, a także wykonywać żadnego kodu. Musi mieć tych uprawnień do tworzenia, wdrażania lub zainstalować pakietu VSPackage.  
  
 Jak najszybciej po jego zainstalowaniu pakietu VSPackage jest w pełni zaufany. Ze względu na wysokim poziomie uprawnień skojarzonych z pakietu VSPackage jest możliwość przypadkowo zainstalowania pakietu VSPackage, który ma złośliwymi działaniami.  
  
 Użytkownikom należy upewnić się, ich instalację pakietów VSPackage tylko z zaufanych źródeł. Firmom tworzenie pakietów VSPackage należy zdecydowanie nazwy i je podpisać, zapewnienie użytkownika, w tym naruszeniu nie będzie mógł. Firmom tworzenie pakietów VSPackage należy sprawdzić ich zależności zewnętrznych, takich jak usługi sieci web i instalacji zdalnej, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.  
  
 Aby uzyskać więcej informacji, zobacz [bezpieczny, wytyczne dotyczące programowania dla platformy .NET Framework](http://msdn.microsoft.com/library/d55zzx87.aspx).  
  
## <a name="see-also"></a>Zobacz także  
 [Dodatek zabezpieczeń](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX zabezpieczeń](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)