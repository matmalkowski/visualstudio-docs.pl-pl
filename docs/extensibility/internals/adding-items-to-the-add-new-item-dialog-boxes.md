---
title: Dodawanie elementów do Dodaj nowy element okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a24a6d531812a170768f8c100f14ad64ab1e68c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Dodawanie elementów do Dodaj nowy element okien dialogowych
Dodawanie elementów do procesu **Dodaj nowy element** okno dialogowe rozpoczyna się od kluczy rejestru. Jak przedstawiono w następujących wpisach rejestru, w sekcji AddItemTemplates zawiera ścieżkę i nazwę katalogu, w które elementy udostępniona w **Dodaj nowy element** są umieszczane okno dialogowe.  
  
> [!NOTE]
>  Tabela natychmiast po segment kodu zawiera dodatkowe informacje na temat wpis rejestru.  
  
 W tej sekcji znajduje się w obszarze [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Pierwszy identyfikator GUID jest CLSID dla projektów tego typu; drugi GUID wskazuje typ projektu zarejestrowanych dla szablonów Dodaj elementy.  
  
 \\\1 \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} {C061DB26-5833-11D2-96F5-000000000000}  
  
 @="#6"  
  
 "TemplatesDir"="\<ścieżki instalacji programu Visual Studio SDK\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|Nazwa|Typ|Dane (z pliku .rgs)|Opis|  
|----------|----------|-----------------------------|-----------------|  
|@ (Ustawienie domyślne)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|Identyfikator zasobu dla **Dodaj element** szablonów.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Ścieżka projektu elementy wyświetlane w oknie dialogowym dla **Dodaj nowy element** kreatora.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Określa porządek sortowania, w węźle drzewa plików wyświetlanych w **Dodaj nowy element** okno dialogowe.|  
  
> [!NOTE]
>  Identyfikatory GUID dla typów projektów Visual C# i Visual Basic są następujące:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Katalog wymienionych w węźle po lewej stronie jest TemplateDirs, czyli % TEMPLATE_PATH%\SomeProjectItems **Dodaj nowy element** drzewa — okno dialogowe. Dodatkowe elementy w drzewie są oparte na podkatalogu w tym katalogu głównego. Pliki można dodać do projektu są elementy w prawym okienku **Dodaj nowy element** okno dialogowe.  
  
 Zazwyczaj ten folder będzie zawierać pliki szablonów w projekcie, takie jak szablon HTML lub pliku .cpp, a wszystkie pliki .vsz uruchamiania kreatorów. Aby kontrolować sposób wyświetlania elementów, mogą również obejmować pliki .vsdir lokalizowanie nazwy katalogów i ikon. Zlokalizowany ciąg jest tekstem, który jest wyświetlany w oknie dialogowym, reprezentujący ten węzeł w drzewie w oknie dialogowym Dodaj nowy element.  
  
 Jednak nie trzeba już wszystko w jednym pliku .vsdir. Może mieć jeden plik .vsdir dla każdego elementu w katalogu. Aby uzyskać więcej informacji, zobacz [kreatora (. Pliku Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) i [opis katalogu szablonu (. Pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Pliki .vsdir w katalogach szablonu są opcjonalne. Jeśli chcesz tylko umieścić element projektu w katalogu i wyświetl ją w **Dodaj nowy element** okno dialogowe, można umieścić tego pliku w katalogu szablonów określona w instrukcji TemplatesDir. Następnie plik zostanie wyświetlona w prawym okienku **Dodaj nowy element** okno dialogowe dla tego projektu. Jednak jeśli chcesz wyświetlić zlokalizowanych podpis dla pliku lub ikony, musi zawierać co najmniej jeden plik .vsdir w katalogu szablonów.  
  
## <a name="grouping-project-items"></a>Grupowanie elementów projektu  
 Jeśli chcesz zawierają grupy szablonu w folderach w **Dodaj nowy element** drzewa okno dialogowe, musi mieć podkatalogów w katalogu głównym szablonu z elementami w nich. Gdy **Dodaj nowy element** okno dialogowe będzie wyświetlana użytkownikom, zostanie również obejrzeć podfoldery i mieć możliwość wyboru elementów projektu z nich.  
  
 Priorytet sortowania w segment kodu Określa, gdzie to katalog szablonu zostanie utworzony w drzewie w odniesieniu do innych elementów węzła drzewa. Aby uzyskać **Dodaj nowy element** okno dialogowe priorytet sortowania jest wszystkie punkty, które należy uwzględnić, tak aby elementy będą wyświetlane w poprawnej lokalizacji w oknie dialogowym.  
  
 Można też wdrożyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfejs do filtrowania wyświetlanych w **Dodaj nowy element** okno dialogowe. Zaimplementowanie interfejsu można skonfigurować jeden szablon katalogu na dysku, który zawiera, na przykład 50 plików kreatora i szablonu. W ten sposób mogą mieć różnych typach projektów z 20 plików, które należą do jednego projektu typu, 30 plików, które należą do innego typu projektu i wszystkich plików w ogólne typu projektu. W ten sposób, w zależności od tego, który projekt został utworzony szablon, można wyświetlić inny zestaw plików szablonów.  
  
 Na przykład w projektach Visual Basic, może być projekty sieci Web i projektów klienckich. Formularze sieci Web nie są przydatne elementy do dodania do projektu klienta i formularze systemu windows nie są przydatne elementy do dodania do projektu serwera sieci Web. W związku z tym można utworzyć jeden katalog szablonu, który zawiera wszystkie pliki dla obu typów projektów. Następnie zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, można ukryć elementy, które nie powinny być wyświetlane na podstawie typu projektu lub ustawienia projektu w projekcie.  
  
## <a name="filtering-project-items"></a>Filtrowanie elementów projektu  
 `IVsFilterAddProjectItemDlg2` udostępnia filtrowania elementów drzewa (lewe okienko) i pliki projektu (po prawej) w następujący sposób:  
  
-   Na podstawie zlokalizowanych nazw (podpisy wyświetlane w oknie dialogowym, który jest zawarty w pliku .vsdir) udzielane przez `IVsFilterAddProjectItemDlg`.  
  
-   Rzeczywiste nazwy plików i folderów na dysku (niezlokalizowana — plik nie .vsdir) udostępniane przez `IVsFilterAddProjectItemDlg`.  
  
-   Według kategorii, dostarczone przez `IVsFilterAddProjectItemDlg2`.  
  
 Aby filtrować według kategorii, podaj kategorii do elementu w pliku .vsdir, takie jak "Formularza sieci Web" lub "Item klienta" w języku Visual Basic. Kod okno dialogowe następnie pobiera klasyfikację kategorii z pliku .vsdir i przekazuje je do Ciebie. Te informacje można następnie przekazać do implementacji `IVsFilterAddProjectItemDlg2` do filtrowania **Dodaj nowy element** okno dialogowe według kategorii. Można również filtrować elementy dla stron sieci Web lub jako przypadków aplikacji Win32 klienta. Ponadto można zidentyfikować [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] oznakowane elementów jako Microsoft Foundation Classes (MFC) lub aktywnego szablonu elementów library (ATL). Po zidentyfikowaniu tych elementów, system projektu można zdefiniować własne klasyfikacje, tak aby systemu można filtrować na podstawie kategorii i klasyfikacji.  
  
 Musisz zaimplementować tę funkcję filtru, nie trzeba mapować tabelę każdy element, który powinien być ukryty. Można po prostu klasyfikowanie elementów w typy i umieść klasyfikacje w .vsdir plik lub pliki. Następnie można ukryć, każdy z elementów, których dotyczy określonej klasyfikacji zaimplementowanie interfejsu. W ten sposób można tworzyć elementy **Dodaj nowy element** dynamiczne okno dialogowe na podstawie stanu w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs dla obiektów, które są zazwyczaj używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Opis katalogu szablonu (. Pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)