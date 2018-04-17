---
title: Fabryki edytora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>Fabryki edytora
Fabryka edytora tworzy Edytor obiektów i umieszczane w ramkę okna, znany jako widoku fizycznego. Tworzy dane dokumentu i obiekty widoku dokumentów, które są niezbędne do utworzenia edytory i projektantów. Fabryka edytora jest wymagane do utworzenia edytorze podstawowych programu Visual Studio i dowolnego edytora standardowego. Opcjonalnie można utworzyć niestandardowego edytora z fabryką edytora.  
  
 Utwórz fabrykę edytora zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Poniższy przykład ilustruje sposób implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> można utworzyć fabryki edytora:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Edytor jest ładowany podczas pierwszego otwierania typu plików obsługiwane przez tego edytora. Można otworzyć edytora określonego lub domyślnego edytora. W przypadku wybrania domyślny edytor zintegrowane środowisko programistyczne (IDE) określa poprawne edytora, aby otworzyć i otwarcie go. Aby uzyskać więcej informacji, zobacz [określania edytor, którego otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Zarejestrowanie fabryki edytora  
 Przed użyciem edytor, który został utworzony, najpierw należy zarejestrować informacje, łącznie z rozszerzeń plików, który może obsługiwać.  
  
 VSPackage są zapisywane w kodzie zarządzanym, należy użyć metody zarządzane pakietu Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> można zarejestrować fabryki edytora po załadowaniu VSPackage. Jeśli VSPackage są zapisywane w kodzie niezarządzane, a następnie fabryką edytora musi zarejestrować za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> usługi.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Rejestrowanie przy użyciu fabryki edytora kodu zarządzanego  
 Należy zarejestrować fabryką edytora w pakiecie VSPackage firmy `Initialize` metody. Pierwsze wywołanie `base.Initialize`, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> dla każdej fabryki edytora  
  
 W kodzie zarządzanym jest niepotrzebna wyrejestrować fabryki edytora, ponieważ pakiet VSPackage to obsłuży. Ponadto jeśli implementuje fabryką edytora <xref:System.IDisposable>, zostanie automatycznie usunięty, gdy jest on zarejestrowany.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Rejestrowanie przy użyciu kodu niezarządzanego fabrykę edytora  
 W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> wdrożenia pakietu edytora, użyj `QueryService` metodę do wywołania `SVsRegisterEditors`. W ten sposób zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody przez przekazanie implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu. Należy najpierw mplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> w osobnej klasy.  
  
## <a name="the-editor-factory-registration-process"></a>Proces rejestracji fabryki edytora  
 Gdy Visual Studio ładuje edytora przy użyciu fabryką edytora odbywa się następujący proces:  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektu wywołań systemowych <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Ta metoda zwraca fabrykę edytora. Visual Studio opóźnienia ładowania pakietu edytora, jednak, aż system projektu rzeczywista wymagana edytora.  
  
3.  Gdy system projektu wymaga edytora, Visual Studio wymaga <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, specjalne metodę, która zwraca zarówno widok dokumentu, jak i w dokumencie obiektów danych.  
  
4.  Jeśli wywołuje przez program Visual Studio do używania fabryki edytora <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> zwrócić zarówno obiekt danych dokumentu i obiekt widoku dokumentu, Visual Studio następnie tworzy okno dokumentu, umieszcza w nim obiektu widoku dokumentu i sprawia, że wpis do uruchomionej dokumentu Tabela (Normalizacją) dla obiekt danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md)