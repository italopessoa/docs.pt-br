---
title: Como criar uma chave no Registro (Visual C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 96d34df3314494fc96ad8b55d7462b67dcc7bd72
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Como criar uma chave no Registro (Visual C#)
Este exemplo adiciona o par de valores, "Name" e "Isabella", ao Registro do usuário atual, sob a chave "Names".  
  
## <a name="example"></a>Exemplo  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Copie o código e cole-o no método `Main` de um aplicativo de console.  
  
-   Substitua o parâmetro `Names` pelo nome de uma chave existente diretamente sob o nó HKEY_CURRENT_USER do Registro.  
  
-   Substitua o parâmetro `Name` pelo nome de um valor que existe diretamente sob o nó Names.  
  
## <a name="robust-programming"></a>Programação robusta  
 Analise a estrutura do Registro para encontrar um local adequado para a chave. Por exemplo, caso você queira abrir a chave Software do usuário atual e criar uma chave com o nome da empresa. Em seguida, adicione os valores do Registro à chave da empresa.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é nulo.  
  
-   O usuário não tem permissões para criar chaves do Registro.  
  
-   O nome da chave excede o limite de 255 caracteres.  
  
-   A chave é fechada.  
  
-   A chave do Registro é somente leitura.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 É mais seguro gravar dados na pasta do usuário — `Microsoft.Win32.Registry.CurrentUser` — em vez de no computador local — `Microsoft.Win32.Registry.LocalMachine`.  
  
 Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir. Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele. Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo. Para impedir isso, use o método `Overload:Microsoft.Win32.RegistryKey.GetValue`. ProcessOnStatus... Ele retornará null se a chave ainda não existir.  
  
 Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACL (listas de controle de acesso).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO?displayProperty=fullName>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)   
 [Ler, gravar e excluir do Registro com C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)

