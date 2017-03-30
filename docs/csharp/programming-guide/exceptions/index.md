---
title: "Exceções e manipulação de exceções (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: 33
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 95563b84f633789fb35eed64c510a11c44b3492b
ms.lasthandoff: 03/13/2017

---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Exceções e manipulação de exceções (Guia de Programação em C#)
Os recursos de manipulação de exceção da linguagem C# ajudam você a lidar com quaisquer situações excepcionais ou inesperadas que ocorram quando um programa for executado. A manipulação de exceção usa as palavras-chave `try`, `catch` e `finally` para executar ações que podem não ser bem-sucedidas, lidar com falhas quando decidir se é razoável fazer isso e limpar recursos posteriormente. As exceções podem ser geradas pelo CLR (Common Language Runtime), pelo .NET Framework ou por quaisquer bibliotecas de terceiros, ou pelo código do aplicativo. As exceções são criadas usando a palavra-chave `throw`.  
  
 Em muitos casos, uma exceção pode ser lançada não por um método que seu código chamou diretamente, mas por outro método mais abaixo na pilha de chamadas. Quando isso acontecer, o CLR desenrolará a pilha, procurando por um método com um bloco `catch` para o tipo de exceção específico e ele será executado primeiro o bloco `catch` que encontrar. Se ele não encontrar um bloco `catch` apropriado na pilha de chamadas, ele encerrará o processo e exibirá uma mensagem para o usuário.  
  
 Neste exemplo, um método testa a divisão por zero e captura o erro. Sem a manipulação de exceção, esse programa encerraria com um **DivideByZeroException não resolvido**.  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Visão geral sobre exceções  
 As exceções têm as seguintes propriedades:  
  
-   As exceções são tipos que derivam, por fim, de `System.Exception`.  
  
-   Use um bloco `try` nas instruções que podem lançar exceções.  
  
-   Quando ocorre uma exceção no bloco `try`, o fluxo de controle vai para o primeiro manipulador de exceção associada que está presente em qualquer lugar na pilha de chamadas. No C#, a palavra-chave `catch` é usada para definir um manipulador de exceção.  
  
-   Se nenhum manipulador de exceção para uma determinada exceção estiver presente, o programa interromperá a execução com uma mensagem de erro.  
  
-   Não capture uma exceção a menos que você possa manipulá-la e deixar o aplicativo em um estado conhecido. Se você capturar `System.Exception`, relance-o usando a palavra-chave `throw` no final do bloco `catch`.  
  
-   Se um bloco `catch` define uma variável de exceção, você pode usá-lo para obter mais informações sobre o tipo de exceção que ocorreu.  
  
-   As exceções podem ser geradas explicitamente por um programa usando a palavra-chave `throw`.  
  
-   Os objetos de exceção contêm informações detalhadas sobre o erro, como o estado da pilha de chamadas e uma descrição de texto do erro.  
  
-   O código em um bloco `finally` será executado mesmo se uma exceção for lançada. Use um bloco `finally` para liberar recursos, por exemplo, para fechar todos os fluxos ou arquivos que foram abertos no bloco `try`.  
  
-   As exceções gerenciadas no .NET Framework são implementadas sobre o mecanismo de manipulação de exceções estruturadas do Win32. Para obter mais informações, consulte [Manipulação de exceções estruturadas (C/C++)](https://docs.microsoft.com/cpp/cpp/structured-exception-handling-c-cpp) e [Curso rápido sobre a manipulação de exceções estruturadas do Win32](http://go.microsoft.com/fwlink/?LinkId=119654).  
  
## <a name="related-sections"></a>Seções relacionadas  
 Consulte os tópicos a seguir para obter mais informações sobre exceções e manipulação de exceção:  
  
-   [Usando exceções](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Tratamento de Exceção](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Criando e lançando exceções](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Exceções geradas pelo compilador](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Como manipular uma exceção usando try/catch (Guia de programação em C#)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Como executar código de limpeza usando finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.SystemException>   
 [Guia de programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [Exceções](http://msdn.microsoft.com/library/f99a1d29-a2a8-47af-9707-9909f9010735)   
 [Hierarquia de exceções](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [Gravando código .NET confiável](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [Minidespejos para exceções específicas](http://go.microsoft.com/fwlink/?LinkId=112408)