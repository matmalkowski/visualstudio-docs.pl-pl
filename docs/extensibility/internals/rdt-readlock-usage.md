---
title: Użycie RDT_ReadLock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131684"
---
# <a name="rdtreadlock-usage"></a>Użycie RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> jest flaga, która zawiera logikę do blokowania dokumentu w systemem dokumentu tabeli (Normalizacją), który znajduje się lista wszystkich dokumentów, które są aktualnie otwarte w programie Visual Studio IDE. Ta flaga Określa, kiedy są otwarte dokumenty i czy dokumentu jest widoczny w interfejsie użytkownika lub przechowywanych w sposób niewidoczny w pamięci.

Ogólnie rzecz biorąc, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> po jest spełniony jeden z następujących czynności:

- Jeśli chcesz otworzyć dokument w sposób niewidoczny i tylko do odczytu, ale go nie jest jeszcze ustalone, które <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> powinien być właścicielem go.

- Jeśli chcesz użytkownikowi monit o zapisanie dokumentów, którą otwarto w sposób niewidoczny przed użytkownika ona wyświetlana w interfejsie użytkownika, a następnie próbował go zamknąć.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak zarządzać widoczna i niewidoczna dokumentów

Po otwarciu dokumentu w interfejsie użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> właściciela dokumentu należy ustanowić i <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> musi zostać ustawiona flaga. Jeśli nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> można ustalić właściciela, a następnie dokumentu nie zostaną zapisane, gdy użytkownik kliknie **Zapisz wszystko** lub zamyka IDE. Oznacza to, jeśli dokument jest otwarty sposób niewidoczny w przypadku, gdy jest on zmodyfikowany w pamięci, a użytkownik jest monit o zapisanie dokumentu podczas zamykania lub zapisany, jeśli **Zapisz wszystko** jest wybrana, a następnie `RDT_ReadLock` nie można użyć. Zamiast tego należy użyć `RDT_EditLock` i Zarejestruj <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> podczas <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> flagi.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock i modyfikacja dokumentu

Flagę poprzedniej wymienionych wskazuje zapewnią niewidoczne otwarcie dokumentu jego `RDT_EditLock` po otwarciu dokumentu przez użytkownika do widocznych **DocumentWindow**. W takiej sytuacji użytkownik zobaczy **zapisać** monitowanie, gdy widoczny **DocumentWindow** jest zamknięty. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementacje, które używają <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> usługi początkowo pracować, gdy tylko `RDT_ReadLock` pochodzi (tj., jeśli dokument jest otwarty w sposób niewidoczny przeprowadzenia analizy informacji o). Później, muszą zostać zmodyfikowane w dokumencie, następnie blokady jest uaktualniany do weak **RDT_EditLock**. Jeśli następnie użytkownik otwiera dokument widoczne **DocumentWindow**, `CodeModel`w słabe `RDT_EditLock` zostanie zwolniony.

Jeśli użytkownik zamknięcie **DocumentWindow** i wybiera **nr** po wyświetleniu monitu, aby zapisać otwartego dokumentu, a następnie `CodeModel` implementacji usuwa wszystkie informacje w dokumencie i ponownie otwiera dokument z dysku w sposób niewidoczny przy następnym więcej informacji jest wymagane dla dokumentu. Subtlety tego zachowania, jest wystąpieniem, gdy użytkownik otwiera **DocumentWindow** niewidoczne otwartego dokumentu, modyfikuje go, zamyka go i następnie wybiera **nr** po wyświetleniu monitu można zapisać dokumentu. W tym przypadku, jeśli dokument ma `RDT_ReadLock`, dokument zostanie faktycznie niemożliwe i zmodyfikowanego dokumentu pozostanie otwarte w sposób niewidoczny w pamięci, nawet jeśli użytkownik wybrał nie można zapisać dokumentu.

Jeśli niewidoczne otwarcie dokumentu używa weak `RDT_EditLock`, a następnie go daje jego blokady po otwarciu dokumentu widoczny i blokady nie są aktywne. Gdy użytkownik zamyka **DocumentWindow** i wybiera **nr** po wyświetleniu monitu można zapisać dokumentu, następnie należy zamknąć dokument z pamięci. Oznacza to, że niewidoczne klienta musi nasłuchiwać zdarzeń Normalizacją do śledzenia to wystąpienie. Podczas następnego dokumentu jest wymagany, musi otwarcia dokumentu.