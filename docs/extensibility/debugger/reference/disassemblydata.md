---
title: DisassemblyData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DisassemblyData
helpviewer_keywords: DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 798ac2d76bb3d9b0bcad2a6dbf7e7aa300030b42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblydata"></a>DisassemblyData
Zawiera opis jednego dezasemblacji instrukcji dla zintegrowane środowisko programistyczne (IDE) do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) stała, która określa pola, które są wypełnione.  
  
 `bstrAddress`  
 Adres przesunięcia od niektórych punkt początkowy (zazwyczaj początku funkcji skojarzone).  
  
 `bstrCodeBytes`  
 Bajtów kodu w tej instrukcji.  
  
 `bstrOpcode`  
 Kod operacji w tej instrukcji.  
  
 `bstrOperands`  
 Argumenty operacji w tej instrukcji.  
  
 `bstrSymbol`  
 Nazwa symbolu, skojarzony z adresem (symboli publicznych, etykiety i tak dalej).  
  
 `uCodeLocationId`  
 Identyfikator lokalizacji kodu dla tego wiersza asemblerze. Jeśli adres kontekst kodu jeden wiersz jest większy niż adres kontekst kodu innego, identyfikator lokalizacji asemblerze kod pierwszego również będzie większy niż drugi identyfikator lokalizacji kodu.  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) odpowiadający pozycji w dokumencie, którym rozpoczyna się dane dezasemblacji.  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) odpowiadający pozycji w dokumencie gdzie kończy się dane dezasemblacji.  
  
 `bstrDocumentUrl`  
 Dla dokumentów tekstowych, które może być reprezentowany jako nazwy pliku `bstrDocumentUrl` pole jest wypełniane nazwę pliku, gdzie można znaleźć źródła, w formacie `file://file name`.  
  
 Dla dokumentów tekstowych, które nie może być reprezentowany jako nazwy pliku `bstrDocumentUrl` jest unikatowym identyfikatorem dla dokumentu, a aparat debugowania musi implementować [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) metody.  
  
 To pole może również zawierać dodatkowe informacje na temat sum kontrolnych. Aby uzyskać więcej informacji, zobacz uwagi.  
  
 `dwByteOffset`  
 Liczba bajtów, jaką instrukcja jest od początku wiersza kodu.  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) stała, który określa flag, które są aktywne.  
  
## <a name="remarks"></a>Uwagi  
 Każdy `DisassemblyData` struktury opisuje jednej instrukcji dezasemblacji. Tablica tych struktur, jest zwracana z [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura jest używana tylko w przypadku opartego na tekście dokumentów. Zakres kod źródłowy dla tej instrukcji jest wypełniane tylko w pierwszej instrukcji, które są generowane na podstawie instrukcji lub wiersza, na przykład, jeśli `dwByteOffset == 0`.  
  
 Dla dokumentów, które są inną niż tekstowa, można uzyskać kontekstu dokumentu z kodu i `bstrDocumentUrl` pole powinno być wartość null. Jeśli `bstrDocumentUrl` pola jest taki sam jak `bstrDocumentUrl` w poprzedniej `DisassemblyData` elementu tablicy, a następnie ustaw `bstrDocumentUrl` ma wartość null.  
  
 Jeśli `dwFlags` pole ma `DF_DOCUMENT_CHECKSUM` Flaga, a następnie informacje dodatkowe sumy kontrolnej następuje ciąg wskazywana przez `bstrDocumentUrl` pola. W szczególności po terminator pusty ciąg jest zgodna algorytm sumy kontrolnej, który z kolei następuje wartość 4-bajtowych wskazującą liczbę bajtów w sumy kontrolnej i który z kolei następuje bajtów sumy kontrolnej identyfikator GUID. Zapoznaj się z przykładem, w tym temacie dotyczące kodowania i dekodowania tego pola w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## <a name="example"></a>Przykład  
 `bstrDocumentUrl` Pole może zawierać dodatkowe informacje inne niż ciąg, jeśli `DF_DOCUMENT_CHECKSUM` flaga jest ustawiona. Proces tworzenia i odczytywania tego ciągu zakodowanego jest prosta w [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]. Jednak w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], jest inny sprawy. Dla tych, którzy są to ciekawi, w poniższym przykładzie przedstawiono jeden ze sposobów tworzenia zakodowanego ciągu z [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] i jednokierunkowej zdekodować ciąg zakodowany w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)