---
title: "Usługi świadczone (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c30c374756578fd71dd344393b58f38cacadeb19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="services-provided-source-control-vspackage"></a>Usługi świadczone (VSPackage kontroli źródła)
Usługi są podstawowego mechanizmu za pośrednictwem której funkcje są udostępniane między VSPackages oraz między Visual Studio zintegrowane środowisko programistyczne (IDE) i jego zainstalowane pakiety VSPackage. Aby uzyskać szczegółowy opis usług i ich znaczenie w środowisku IDE programu Visual Studio, zobacz[Using i dostarczanie usług](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Usługi kontroli źródła  
 Program Visual Studio oferuje dwie warstwy usług, usług poziomu IDE i poziom pakietu usług. Środowiska IDE programu Visual Studio udostępnia natywnie IDE poziomu usługi. Pakiet kontroli źródła zużywa niektóre z tych usług. Pakiet kontroli źródła jako pakiet VSPackage udostępnia jego funkcja kontroli źródła dostarczając usługi kontroli źródła prywatnej własnych. Pakiet kontroli źródła hermetyzuje zbiór związanych z kontroli źródła w interfejsy implementowane przez go w formie kontraktu, który może być używany przez środowiska IDE programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)