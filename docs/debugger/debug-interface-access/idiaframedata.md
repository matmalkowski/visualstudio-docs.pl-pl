---
title: Idiaframedata — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: efdc99d45bfc081fafd9b8467937567cca777b68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedata"></a>IDiaFrameData
Przedstawia szczegóły ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaFrameData`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Pobiera część sekcji kod adres ramki.|  
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Pobiera przesunięcia część adresu kodu ramki.|  
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Pobiera obraz wirtualny adres względny (RVA) kodu ramki.|  
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Pobiera wirtualnego adresu (VA) kod ramki.|  
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Pobiera długość w bajtach bloku kodu opisanego przez ramki.|  
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Pobiera liczbę bajtów zmiennych lokalnych wypychana na stosie.|  
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Pobiera liczbę bajtów parametrów wypychana na stosie.|  
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Pobiera maksymalną liczbę bajtów wypychana na stosie w ramce.|  
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Pobiera liczbę bajtów prologu kod w bloku.|  
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Pobiera liczbę bajtów zapisanych rejestrów wypychana na stosie.|  
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Pobiera ciąg program, który jest używany do obliczania rejestru ustawić przed wywołaniem do bieżącej funkcji.|  
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Pobiera flagę wskazującą, obsługa wyjątków w tym system jest włączona.|  
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Pobiera flagę wskazującą, że obsługa wyjątków C++ jest włączona.|  
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.|  
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Pobiera flagę wskazującą, czy wskaźnik podstawowy jest przydzielona dla kodu tego zakresu adresów. Ta metoda jest przestarzała.|  
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Pobiera typ ramki specyficznych dla kompilatora.|  
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Pobiera ramek danych interfejsu dla funkcji otaczającej.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Wykonuje odwijanie stosu i zwraca bieżący stan rejestrów w interfejsie ramki przeszukiwania stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Szczegóły dostępne dla ramki są punktów wykonywania w zakresie adresów wskazuje długość adresu i bloku.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie przez wywołanie metody tego interfejsu [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) lub [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) metody. Zobacz [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) interfejsu, aby uzyskać szczegółowe informacje.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie drukowane limit właściwości `IDiaFrameData` obiektu. Zobacz [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) interfejsu, na przykład przedstawia sposób `IDiaFrameData` są uzyskiwane interfejsu.  
  
```C++  
void PrintFrameData(IDiaFrameData* pFrameData){  
    DWORD dwSect;  
    DWORD dwOffset;  
    DWORD cbBlock;  
    DWORD cbLocals; // Number of bytes reserved for the function locals  
    DWORD cbParams; // Number of bytes reserved for the function arguments  
    DWORD cbMaxStack;  
    DWORD cbProlog;  
    DWORD cbSavedRegs;  
    BOOL  bSEH;  
    BOOL  bEH;  
    BOOL  bStart;  
    BSTR  wszProgram;  
  
    if(pFrameData->get_addressSection(&dwSect) == S_OK &&   
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&  
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&  
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&  
       pFrameData->get_lengthParams(&cbParams) == S_OK &&  
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&  
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&  
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&  
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&  
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&  
       pFrameData->get_functionStart(&bStart) == S_OK )  
    {  
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);  
        wprintf(L"Block size     : 0x%8X\n", cbBlock);  
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);  
        wprintf(L"Parms size     : 0x%8X\n", cbParams);  
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);  
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);  
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);  
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');  
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');  
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');  
  
        if (pFrameData->get_program(&wszProgram) == S_OK)  
        {  
            wprintf(L"Program used for register set: %s\n", wszProgram);  
            SysFreeString(wszProgram);  
        }  
        else  
        {  
            wprintf(L"\n");  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)