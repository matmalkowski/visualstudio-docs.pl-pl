---
title: Ważne poleceń języka usługi filtry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="important-commands-for-language-service-filters"></a>Ważne poleceń dla filtrów usługi języka
Aby utworzyć filtr usługi języka oferujący wszystkie potrzebne funkcje, należy rozważyć obsługi następujących poleceń. Pełną listę identyfikatory poleceń jest zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenie dla kodu zarządzanego i nagłówek Stdidcmd.h plik niezarządzanych [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kodu. Można znaleźć w pliku Stdidcmd.h *ścieżki instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Polecenia do dojścia  
  
> [!NOTE]
>  Nie jest to konieczne do filtrowania dla każdego polecenia w poniższej tabeli.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik kliknie prawym przyciskiem myszy. To polecenie wskazuje, czy nadszedł czas, aby zapewnić menu skrótów. Jeśli nie obsługują tego polecenia, Edytor tekstu zawiera domyślne menu skrótów bez żadnych poleceń specyficzny dla języka. Aby uwzględnić poleceniach w tym menu, obsługi polecenia i wyświetlić menu skrótów samodzielnie.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze CTRL + J. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pokazanie pole uzupełniania instrukcji.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze znak. Monitorowanie to polecenie, aby określić po wpisaniu znaku wyzwalacza i zapewnienie instrukcji zakończenia, metody porady i znacznikach tekstu, takich jak kolorowanie składni, nawiasy dopasowywania i znaczniki błędu. Wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zatwierdzające uzupełnienie instrukcji i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> porady metody. Aby obsługiwać znacznikach tekstu, monitorować to polecenie, aby określić, czy znak jest wpisany wymaga zaktualizowanie znaczniki sieci.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz Enter. Monitorowanie tego polecenia do określenia, kiedy odrzucić okno Porada metody wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widoku tekstu obsługuje tego polecenia.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisza. Monitor do określenia, kiedy odrzucić okno Porada metody wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widoku tekstu obsługuje tego polecenia.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu lub klawisza skrótu. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aktualizowania okna Porada przy użyciu parametrów.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik znajduje się nad zmiennej lub umieszcza kursor w zmiennej i wybiera **szybka podpowiedź** z **IntelliSense** w **Edytuj** menu. Zwraca typ zmiennej w etykietce przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Jeśli debugowanie jest aktywny, porady powinien zawierają wartości zmiennej.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze klawisze CTRL + SPACJA. To polecenie informuje usługa języka aby wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu, zwykle **Zaznaczanie komentarzy** lub **usuń znaczniki komentarza wybór** z **zaawansowane** w **Edytuj** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Wskazuje, że użytkownik chce komentarz zaznaczonego tekstu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce usuń znaczniki komentarza zaznaczonego tekstu. Te polecenia może być zaimplementowany tylko przez usługi języka.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)