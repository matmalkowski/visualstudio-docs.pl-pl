---
title: "Idiasymbol — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c35accc7ca75a987dae615c06df68b4f85bba4a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbol"></a>IDiaSymbol
Opisuje właściwości instancji symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>Metody w porządku alfabetycznym  
 W poniższej tabeli przedstawiono metody `IDiaSymbol`.  
  
> [!NOTE]
>  Symbole zwróci istotnych danych tylko niektóre z tych metod, w zależności od typu symbolu. Jeśli metoda zwraca `S_OK`, a następnie metoda zwróciła istotnych danych.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Pobiera wszystkie elementy podrzędne symbolu.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Pobiera elementy podrzędne symbolu. Ta metoda jest rozszerzona wersja [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe na określony adres.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe w określonej wirtualnej adresem względnym (RVA).|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe na określony adres wirtualny.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane w podanym adresem.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane w określonej wirtualnej adresem względnym (RVA).|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane na określony adres wirtualny (VA).|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Pobiera wyliczenie umożliwia klientowi Iterowanie za pomocą informacji o numerze linii wszystkie funkcje, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonego zakresu adresów.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonej wirtualnej adres względny (RVA).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonego wirtualnego adresu (VA).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Biorąc pod uwagę odpowiadającą mu wartość tagu, ta metoda zwraca wyliczenie symboli, które są zawarte w tej funkcji stub pod określonym adresem względnym wirtualnego.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Zwraca liczbę tagów wskaźnika akceleratora w funkcji stub C++ AMP.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Zwraca wszystkie akceleratora wskaźnika tagu wartości odpowiadających funkcji stub akceleratora C++ AMP.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Pobiera modyfikator dostępu elementu członkowskiego klasy.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Pobiera przesunięcia część adresu.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Pobiera część adresu w sekcji.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Pobiera flagę wskazującą, czy inny symbol odwołuje się ten adres.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Pobiera wartość wieku programu bazy danych.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Pobiera identyfikator symbol typu indeksu tablicy.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Pobiera identyfikator typu indeksu tablicy symbolu.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Pobiera numer wersji głównej zaplecza.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Pobiera zaplecza podrzędny numer wersji.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Pobiera numer kompilacji zaplecza.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Pobiera Przesunięcie danych podstawowych.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Pobiera miejsca danych podstawowych.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Pobiera symbol, z której jest oparty wskaźnik.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Pobiera identyfikator symbolu, z której jest oparty wskaźnik.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Pobiera typ tagu typu prostego.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Pobiera Pozycja bitu lokalizacji.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Pobiera wbudowanych rodzaj typu HLSL.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Zwraca wskaźnik konwencja wywołania metody.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Pobiera odwołanie do klasy obiektu nadrzędnego symbolu.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Pobiera identyfikator klasy nadrzędnej symbolu.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Pobiera flagę wskazującą, czy symbol odwołuje się do adresu kodu.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Pobiera flagę wskazującą, czy symbol został wygenerowany przez kompilator.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Pobiera nazwę kompilatora używany do tworzenia [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika konstruktora.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Pobiera zawierającego symbol tego symbolu.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest stały.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Pobiera liczbę elementów listy lub tablicy.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Pobiera liczbę zakresów prawidłowy adres skojarzony z lokalnym symbolu.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Pobiera flagę wskazującą, czy funkcja używa konwencji wywoływania niestandardowych.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Pobiera z jaką bajty danych symbolu OEM.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Pobiera zmiennej klasyfikacji symbolu danych.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Pobiera flagi opisujące funkcji Edytuj i Kontynuuj program skompilowanych lub jednostki.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Pobiera flagę wskazującą, czy funkcja używa dalekiego powrotu.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Pobiera numer wersji głównej frontonu.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Pobiera frontonu podrzędny numer wersji.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Pobiera numer kompilacji frontonu.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Pobiera flagę wskazującą, czy symboli publicznych odwołuje się do funkcji.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Pobiera identyfikator GUID symbolu.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Pobiera flagę wskazującą, czy funkcja zawiera wywołanie `alloca`.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Pobiera flagę wskazującą, czy wszystkie operatory przypisania zdefiniowany typ danych zdefiniowany przez użytkownika.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Pobiera flagę wskazującą, czy wszystkie operatory rzutowania zdefiniowany typ danych zdefiniowany przez użytkownika.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Pobiera flagę wskazującą, czy compiland zawiera wszystkie informacje o debugowaniu.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Pobiera flagę wskazującą, czy funkcja obsługi wyjątków C++ stylu.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Pobiera flagę wskazującą, czy funkcja obsługi wyjątków asynchronicznych.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Pobiera flagę wskazującą, czy funkcja ma wbudowany zestaw.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Pobiera flagę wskazującą, czy funkcja zawiera polecenie longjmp (część obsługi wyjątków w stylu języka C).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Pobiera flagę wskazującą, czy moduł zawiera kodu zarządzanego.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Pobiera flagę wskazującą, czy definicje typów ma zagnieżdżonego organizatora typu danych zdefiniowanego przez użytkownika.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Pobiera flagę wskazującą, czy funkcja lub compiland skompilowany w kontroli zabezpieczeń (za pośrednictwem [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) przełącznika kompilatora).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Pobiera flagę wskazującą, czy funkcja Win32 stylu strukturalnych sposób obsługi wyjątków.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Pobiera flagę wskazującą, czy funkcji zawiera polecenia setjmp.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest pośrednia wirtualna klasa podstawowa.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Pobiera flagę wskazującą, czy funkcja została oznaczona atrybutem wbudowanego.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Pobiera flagę wskazującą, czy funkcja ma typ zwracany przerwanie instrukcji.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Pobiera flagę wskazującą, czy funkcja jest funkcją wirtualną klasę podstawową.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Pobiera flagę wskazującą, czy symbol odpowiada grupie udostępnionego zmienną lokalną w kodzie skompilowanym dla akcelerator programu C++ AMP.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Pobiera flagę wskazującą, czy symbol odpowiada *definicji symbolu zakresu* składnika tag zmiennej wskaźnikowej w kodzie skompilowanym dla C++ AMP akceleratora. Symbol zakresu definicji jest lokalizacja zmiennej dla zakresu adresów.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Wskazuje, czy symbol odpowiada symbolem funkcji najwyższego poziomu dla modułu skompilowanego dla akceleratora, który odpowiada `parallel_for_each` wywołania.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Pobiera flagę wskazującą, czy w danych jest częścią agregacją wiele symboli.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Pobiera flagę wskazującą, czy plik symboli zawiera typy C.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Pobiera flagę wskazującą, czy moduł został przekonwertowany z typowych pośredniego języka (CIL) do kodu natywnego.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Pobiera flagę wskazującą, czy elementy typu danych zdefiniowanego przez użytkownika są wyrównane do określonych granic.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Określa, czy ta ikona reprezentuje dane wysokiego poziomu programu do cieniowania języka (HLSL).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Pobiera flagę wskazującą, czy moduł został skompilowany z [/hotpatch (Utwórz obraz możliwych)](/cpp/build/reference/hotpatch-create-hotpatchable-image) przełącznika kompilatora.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Pobiera flagę wskazującą, czy zarządzany compiland został połączony z LTCG konsolidatora.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Określa, czy macierz głównych wiersza.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Pobiera flagę wskazującą, czy zarządzany compiland jest modułu .netmodule (tylko metadane zawierające).|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Określa, czy `this` wskazuje wskaźnik do elementu członkowskiego danych z wielu dziedziczenia.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Pobiera flagę wskazującą, czy funkcja [naked](/cpp/cpp/naked-cpp) atrybutu.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Określa, czy zmienna jest w celu optymalizacji.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Określa, czy `this` wskaźnika jest oparta na wartości symbolu.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Określa, czy ten symbol jest wskaźnik do elementu członkowskiego danych.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Określa, czy ten symbol jest wskaźnikiem do funkcji członkowskiej.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Określa, czy zmienna wykonuje wartość zwracaną.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Określa, czy moduł jest skompilowana przy użyciu opcji/SDL.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Określa, czy `this` wskazuje wskaźnik do elementu członkowskiego danych z jednego dziedziczenia.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Pobiera flagę wskazującą, czy dane podzielone na agregacji oddzielne symboli.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Pobiera flagę wskazującą, czy funkcja lub thunk warstwę jest statyczne.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Pobiera flagę wskazującą, czy symboli prywatnych ma zostały usunięte z pliku symboli.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Określa, czy `this` wskazuje wskaźnik do elementu członkowskiego danych z wirtualnego dziedziczenia.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Pobiera języka źródłowego.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Pobiera liczbę bajtów pamięci używanej przez obiekt reprezentowany przez ten symbol.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Pobiera odwołanie do elementu nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Pobiera identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Pobiera nazwę pliku biblioteki lub obiekt, z której została załadowana obiektu.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Zwraca długość zakresu adresów, w którym symbol lokalnego jest poprawna.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Zwraca część sekcji początkowy zakres adresów, w którym symbol lokalnego jest poprawna.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Zwraca przesunięcia część początkowy zakres adresów, w którym symbol lokalnego jest poprawna.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Zwraca początek zakresu adresów, w którym symbol lokalnego jest poprawna.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Pobiera typ lokalizacji symbolu danych.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Pobiera dolna granica FORTRAN wymiaru tablicy.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Pobiera identyfikator symbol dolna granica FORTRAN wymiaru tablicy.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Pobiera typ elementu docelowego procesora CPU.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Pobiera flagę czy wskazującą, czy symbol odwołuje się do kodu zarządzanego.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Pobiera rodzaj miejsca w pamięci.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Pobiera flagę wskazującą, czy symbol odwołuje się do kodu Microsoft języka pośredniego (MSIL).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Pobiera nazwę symbolu.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Pobiera flagę wskazującą, czy jest zagnieżdżony typ danych zdefiniowany przez użytkownika.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Pobiera flagę wskazującą, czy funkcja jest oznaczony atrybutem [noinline](/cpp/cpp/noinline) atrybutu.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Pobiera flagę wskazującą, czy funkcja została zadeklarowana z [noreturn](/cpp/cpp/noreturn) atrybutu.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Pobiera flagę wskazującą, czy kolejność stosu nie może być wykonywane w ramach sprawdzania bufora stosu.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Pobiera flagę wskazującą, czy funkcja lub etykiety nigdy nie zostanie osiągnięty.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Zwraca liczbę tagów wskaźnika akceleratora w funkcji stub C++ AMP.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Pobiera liczbę modyfikatory, które są stosowane do oryginalnego typu.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Pobiera liczbę indeksów rejestru.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Pobiera liczbę wierszy w macierzy.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Pobiera liczbę kolumn w macierzy.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Pobiera nazwę pliku obiektu.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Pobiera typ wskaźnika obiektu dla metody klasy.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Pobiera symbolu `oemId` wartość.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Pobiera symbolu `oemSymbolId` wartość.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Pobiera przesunięcie Lokalizacja symbolu.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Pobiera flagę wskazującą, czy funkcja lub etykieta zawiera kod zoptymalizowany również jako informacje o debugowaniu.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Pobiera flagę wskazującą, czy typ danych ma skonfigurowane przeciążone operatory.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Pobiera flagę wskazującą, czy spakowane typ danych zdefiniowany przez użytkownika.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Pobiera typ platformy, dla którego program lub compiland został skompilowany.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Pobiera flagę tego wskazująca, czy funkcja jest czysty wirtualnego.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Pobiera rangę tablicy wielowymiarowej FORTRAN.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Pobiera flagę wskazującą, czy typ wskaźnika jest odwołanie.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Pobiera oznaczeniem rejestru lokalizacji.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Pobiera typ rejestru.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Pobiera wirtualny adres względny (RVA) lokalizacji.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Określa, czy `this` wskaźnika jest oznaczony jako ograniczone.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Pobiera miejsca przykłady.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika pojawia się w zakresie leksykalne nieglobalnych.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Pobiera wartość podpisu symbolu.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Pobiera informacje o rozmiarze elementu członkowskiego typu zdefiniowanego przez użytkownika.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Pobiera numer gniazda lokalizacji.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Pobiera nazwę pliku źródłowego.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Pobiera numer źródłowego plików i wierszy, wskazujące, w którym zdefiniowana jest określonego typu zdefiniowane przez użytkownika.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Pobiera krok macierzy lub strided tablicy.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Pobiera typ sub.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Pobiera identyfikator typu sub.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Pobiera nazwę pliku, z którego symbole zostały załadowane.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Pobiera identyfikator unikatowy symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Pobiera klasyfikatora typ symbolu.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Pobiera sekcji przesunięcia docelowego thunk.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Pobiera wirtualny adres względny (RVA) docelowego thunk.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Pobiera sekcja adresu docelowego thunk.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Pobiera wirtualnego adresu docelowego thunk (VA).|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Pobiera miejsca tekstury.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Pobiera logicznym `this` adjustor dla metody.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Pobiera typ thunk funkcji.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Pobiera sygnatury czasowej pliku wykonywalnego.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Pobiera token metadanych zarządzanego funkcji lub zmienna.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Pobiera odwołanie do sygnatury funkcji.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Pobiera identyfikator typu symbolu.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Pobiera tablicę wartości typu kompilatora specyficzne dla tego symbolu.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Pobiera tablicę wartości identyfikatora typu kompilatora specyficzne dla tego symbolu.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Pobiera uav miejsca.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Pobiera różnych typów zdefiniowanych przez użytkownika (UDT).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest niewyrównany.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Pobiera nazwę bez C++ dekorowane, lub połączenie, nazwę.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Rozszerzenie `get_undecoratedName` metodę, która pobiera nazwę bez na podstawie wartości pola rozszerzenie.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Pobiera identyfikator oryginalnego typu (bez modyfikacji).|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Pobiera górna granica FORTRAN wymiaru tablicy.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Pobiera identyfikator symbol górna granica FORTRAN wymiaru tablicy.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Pobiera wartość stałą.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Pobiera flagę wskazującą, czy funkcja jest wirtualna.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Pobiera adres wirtualny lokalizacji (VA).|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest wirtualna klasa podstawowa.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Pobiera indeks tabeli wirtualnej przemieszczenie podstawowej.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Pobiera przesunięcie w tabeli funkcji wirtualnych z funkcją wirtualną.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Pobiera przesunięcie wirtualnego wskaźnik podstawowy.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Pobiera typ wskaźnika wirtualnego tabeli podstawowej.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Pobiera interfejs symbol typu tabeli wirtualnej dla typu zdefiniowanego przez użytkownika.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Pobiera identyfikator kształtu tabeli wirtualnej symbolu.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest nietrwały.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskaj tego interfejsu, wywołując jedną z następujących metod:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób wyświetlania zmiennych lokalnych dla funkcji pod danym adresem względnym wirtualnego. Pokazuje też, jak symbole różne typy są ze sobą powiązane.  
  
> [!NOTE]
>  `CDiaBSTR`jest klasa, która opakowuje `BSTR` i automatycznie obsługuje zwalnianie ciąg, gdy podczas tworzenia wystąpienia wykracza poza zakres.  
  
```C++  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 `Header:`Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsymbolsbyaddr —](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Jednostka kompilacji](../../debugger/debug-interface-access/compiland.md)