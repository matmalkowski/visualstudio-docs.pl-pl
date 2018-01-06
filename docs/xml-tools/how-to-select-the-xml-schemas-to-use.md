---
title: "Porady: Wybieranie schematów XML do użycia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 80d0438e7c7dfb7fd346dc5faae6f364279658ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Porady: Wybieranie schematów XML do użycia
Edytor XML zawiera pamięci podręcznej schematu znajduje się w katalogu %InstallDir%\Xml\Schemas. Pamięci podręcznej schematu obejmuje dobrze znanych schematów XML, które są używane do walidacji dokumentu IntelliSense i XML.  
  
 **Schematy** właściwości dokumentu jest używana do wybierania co najmniej jeden schemat definition language (XSD) schematy XML do użycia. Można wybrać schematów z pamięci podręcznej schematu lub określ schemat, który nie znajduje się w pamięci podręcznej.  
  
 Schematów, które określisz są zapisywane w ukrytym pliku opcji użytkownika rozwiązania (.suo), oraz wszystkie inne właściwości dokumentu XML. W związku z tym nie trzeba ponownie wprowadzić te wartości przy następnym otwarciu rozwiązania.  
  
> [!NOTE]
>  Edytor można sprawdzić za pomocą wbudowanego schematu lub schemat odwołuje się `xsd:schemaLocation` atrybutu. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności kodu XML dokumentu](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Aby wybrać schematu XML z pamięci podręcznej schematu  
  
1.  Otwórz plik w edytorze XML.  
  
2.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.  
  
     **Schematów XML** zostanie wyświetlone okno dialogowe. Okno dialogowe zawiera listę wszystkich schematów z rozszerzeniem xsd w pamięci podręcznej schematu (w tym schematów, do którego odwołuje się plik catalog.xml), a także żadnego schematu, który znajduje się w bieżącym rozwiązaniu, Otwórz w programie Visual Studio, do którego odwołuje się `xsd:schemaLocation` atrybut lub do których odwołuje się **schematy** właściwości.  
  
3.  Wybierz schematy do użycia w celu weryfikacji, wykonując jedną z następujących czynności:  
  
    -   Wybierz na liście schemat **schematów XML** okna dialogowego, kliknij przycisk **użyj** kolumny, a następnie wybierz **używają tego schematu**.  
  
     —lub—  
  
    -   Wybierz wiele schematów na liście **schematów XML** okna dialogowego, kliknij prawym przyciskiem myszy i wybierz **używają tego schematu**.  
  
4.  Kliknij przycisk **OK**.  
  
     Lista wybranych schematów jest kopiowany do **schematy** właściwości dokumentu.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Aby dodać schematu XML do pamięci podręcznej schematu  
  
1.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.  
  
2.  Kliknij przycisk **Dodaj**.  
  
     Spowoduje to otwarcie **Otwórz schematu XSD** okna dialogowego.  
  
3.  Wyszukaj i wybierz schematy do dodania do pamięci podręcznej schematu.  
  
4.  Kliknij przycisk **Otwórz**.  
  
     Schematy dodane do schematu pamięci podręcznej i jest **użyj** ma ustawioną wartość w kolumnie **używają tego schematu**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Aby usunąć z pamięci podręcznej schematu schematu XML  
  
1.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.  
  
2.  Wybierz schemat, Usuń, a następnie kliknij przycisk **Usuń**.  
  
     Schemat zostanie usunięty z pamięci podręcznej schematu w pamięci, ale nie zostanie usunięta z systemu plików.  
  
    > [!NOTE]
    >  Jeśli nadal masz odwołanie do schematu za pomocą `schemaLocation` atrybutu lub odpowiadającego mu `targetNamespace` następnie **Usuń** nie będzie działać w tej sytuacji z powodu skojarzenia automatycznie. W takim przypadku zalecane jest, aby oznaczyć schematu jako **nie używaj wybranych schematów** w **użyj** kolumny.  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięci podręcznej schematów](../xml-tools/schema-cache.md)   
 [Okno dialogowe schematy XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Edytor XML](../xml-tools/xml-editor.md)