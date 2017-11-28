---
title: "Implémentation d’une méthode Seek dans un composant de Pipeline en continu géré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline interfaces, IStream interface
- pipeline components [custom], code samples
- IStream interface
- Seek method
ms.assetid: 2e546c41-822d-4e22-a8f6-8959072ef3d2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5181957f691502dcc2b09a367c31de575097d1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-a-seek-method-in-a-managed-streaming-pipeline-component"></a><span data-ttu-id="637ed-102">Implémentation d’une méthode Seek dans un composant de Pipeline managé de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="637ed-102">Implementing a Seek Method in a Managed Streaming Pipeline Component</span></span>
<span data-ttu-id="637ed-103">Natif **IStream** interface ne fournit pas une méthode pour vérifier la position actuelle du flux, par conséquent, le moteur de messagerie utilise les éléments suivants **recherche** (méthode).</span><span class="sxs-lookup"><span data-stu-id="637ed-103">The native **IStream** interface does not provide a method to check the current stream position, so the messaging engine uses the following **Seek** method.</span></span>  
  
```  
pStream->Seek(0, STREAM_SEEK_CUR, &pNewPosition);  
```  
  
 <span data-ttu-id="637ed-104">Cette méthode ne déplace pas le pointeur de flux mais elle recherche la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="637ed-104">This method does not move the stream pointer; instead it queries the current position.</span></span> <span data-ttu-id="637ed-105">Si vous implémentez un composant de pipeline qui fonctionne avec un flux non identifiable, vous pouvez utiliser la **Stream.Seek** méthode comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="637ed-105">So if you implement a pipeline component that works with a nonseekable stream, you can use the **Stream.Seek** method as in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="637ed-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="637ed-106">Example</span></span>  
  
```csharp  
override public long Seek(long offset, SeekOrigin origin)  
{  
   long pos = -1;  
  
   switch(origin)  
   {  
      case SeekOrigin.Begin :  
         pos = offset;  
         break;  
      case SeekOrigin.Current :  
         pos = Position + offset;  
         break;  
      case SeekOrigin.End :  
         break;  
   }  
  
   // We generally disallow seeking of the stream  
   // However, in unmanaged code, many people use Seek(0,CURR) to retrieve    // the current position  
   // Special case (that is, if Seek does not change position, do not   
   // throw an exception)  
   if (pos==Position)  
   {  
      return pos;  
   }  
   else  
   {  
      throw new NotSupportedException("ForwardOnlyEventingReadStream does not support Seek()");  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="637ed-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="637ed-107">See Also</span></span>  
 [<span data-ttu-id="637ed-108">Développement de composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="637ed-108">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)