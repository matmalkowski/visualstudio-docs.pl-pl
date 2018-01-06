---
title: "Vsgdbg — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1a3810f6f0c2de6bffb2f97c2f1fc446ea3b6d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
Reprezentuje interfejs dla sterowanie programowe składnika w aplikacji diagnostyki grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `VsgDbg` Klasa obsługuje następujące elementy członkowskie.  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Tworzy wystąpienie klasy `VsgDbg` klasy i opcjonalnie przygotowuje składników w aplikacji diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|  
|[VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienia `VsgDbg` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Dodaje niestandardowy komunikat do diagnostyki grafiki HUD (wyświetlanie Head-Up).|  
|[BeginCapture](begincapture.md)|Rozpoczyna się interwał przechwytywania, który będzie kończyć się `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Przechwytuje pozostałej części bieżącej ramki do pliku dziennika grafiki.|  
|[Kopiowanie (przechwycenie programowe)](copy-programmatic-capture.md)|Kopiuje zawartość pliku dziennika (.vsglog) Grafika aktywna do nowego pliku.|  
|[EndCapture](endcapture.md)|Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.|  
|[Init](init.md)|Przygotowuje składników w aplikacji diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|  
|[ToggleHUD](togglehud.md)|Włącza/wyłącza nakładki HUD diagnostyki grafiki lub wyłączyć.|  
|[UnInit](uninit.md)|Kończenie znajdujących się w pliku dziennika grafiki, zamyka i zwalnia zasoby, które były używane podczas aplikacji został aktywnie rejestrowanie informacji graficznych.|  
  
## <a name="remarks"></a>Uwagi  
 `VsgDbg` Klasa reprezentuje interfejs, który służy do kontrolowania funkcji diagnostyki grafiki programowo. Niektóre funkcje mogą być używane nawet wtedy, gdy nie są aktywnie jest przechwytywanie i rejestrowanie informacji graficznych; obejmuje to `AddMessage` funkcji członkowskiej i `ToggleHUD` funkcję elementu członkowskiego. Inne funkcje Członkowskie przygotowanie składnika diagnostyki grafiki, aby uruchomić lub zatrzymać active przechwytywanie informacji graficznych w aplikacji lub musi zostać wywołana, gdy aplikacja jest aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki.