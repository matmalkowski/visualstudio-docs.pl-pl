---
title: "Projekt trwałości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>Trwałość projektu
Trwałości jest kluczy dla projektu. Elementy projektu, które reprezentują plików; użyj większości projektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje również projektów, w których dane są nie opartych na pliku. Musi zostać utrwalony plików należących do projektu i pliku projektu. IDE powoduje, że projekt, aby zapisać siebie lub elementu projektu.  
  
 Szablony projektów są przekazywane do fabryki projektu. Szablony powinien obsługiwać inicjowanie wszystkich elementów projektu, zgodnie z wymaganiami typu określonego projektu. Szablony te można później zapisywane jako pliki projektu i zarządza IDE za pośrednictwem rozwiązania. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień przez za pomocą fabryk projektów przez ustawienie](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) i [rozwiązań](../../extensibility/internals/solutions.md).  
  
 Elementy projektu może być opartych na plikach lub systemem plików:  
  
-   Elementy opartej na plikach może być lokalnym lub zdalnym. W przypadku projektów sieci Web w języku C# na przykład połączenia z plikami w systemie zdalnym utrwalić lokalnie, należy zachować same pliki w systemie zdalnym.  
  
-   Elementy na podstawie pliku nie można zapisać elementów do bazy danych lub repozytorium.  
  
## <a name="commit-models"></a>Zatwierdź modeli  
 Po podjęciu decyzji, w którym znajdują się elementy projektu, należy wybrać odpowiednie zatwierdzania modelu. Na przykład w modelu opartych na plikach z lokalnych plików, każdy projekt zapisaniem samodzielnie. W modelu repozytorium możesz zapisać kilka elementów w jednej transakcji. Aby uzyskać więcej informacji, zobacz [decyzji projektowych typ projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
 Aby określić rozszerzenia nazw plików, zaimplementuj projekty <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejsu, która dostarcza informacje umożliwiające klientowi implementacji obiektu **Zapisz jako** okno dialogowe — oznacza to, aby wypełnić **Zapisz jako typ**  rozwijania listy i zarządzanie nimi rozszerzenie nazwy pliku początkowej.  
  
 Wywołania IDE `IPersistFileFormat` jako odpowiednie elementy interfejsu na projekt, aby wskazać, że projekt ma utrwalić jego projektu. W związku z tym obiektem jest właścicielem wszystkich aspektów jego plik i format. W tym nazwę formatu obiektu.  
  
 W przypadku, gdy elementy nie są plikami `IPersistFileFormat` jest nadal jak plik nieopartych elementy są zachowywane. Pliki, takie jak pliki .vbp dla projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektów lub .vcproj pliki [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów, musi również zostać utrwalony.  
  
 Do zapisania akcje, IDE sprawdza uruchomionej tabeli dokumentów (Normalizacją) i hierarchii przekazuje polecenia do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfejsów. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> — Metoda jest zaimplementowana w celu ustalenia, czy element został zmieniony. Jeśli element ma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> zaimplementowano metody zapisać zmodyfikowanego elementu.  
  
 Metody w `IVsPersistHierarchyItem2` interfejsu są używane do ustalenia, czy element może zostać ponownie załadowana i, jeśli element można załadować go ponownie. Ponadto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metody mogą zostać wdrożone zmienionych elementów do usunięcia, bez zapisywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Tworzenie wystąpień projektu za pomocą fabryk projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)