---
title: "Méthode GetSchema de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c83340c-a775-435c-9633-3a692611e99e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c40e698b3c373aa4e10a8de2362650a42e71a1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-getschema-method"></a>Méthode GetSchema de l'adaptateur
Supposons que le fichier WSDL référencé ne contienne que des références de schéma et aucun schéma incorporé. Dans ce cas, vous utilisez la **GetSchema** méthode de la **IAdapterConfig** interface pour charger un schéma référencé à partir d’un fichier WSDL.  
  
 Dans l’exemple d’adaptateur file, modifiez le code dans le **GetSchema** méthode du fichier AdapterManagement.cs afin de retourner des fichiers XSD externes qui ne sont pas inclus dans les fichiers WSDL.  
  
 Le code suivant est issu le **GetSchema** méthode du fichier AdapterManagement.cs. La valeur retournée est null, car le fichier Service1.wsdl contient des schémas incorporés. Si cela n'avait pas été le cas, une chaîne correspondant à un fichier de schéma XSD aurait été retournée.  
  
```  
/// <summary>  
        /// Acquire externally referenced xsd's  
        /// </summary>  
        /// <param name="xsdLocation">Location of schema</param>  
        /// <param name="xsdNamespace">Namespace</param>  
        /// <param name="XSDFileName">Schmea file name (return)</param>  
        /// <returns>Outcome of acquisition</returns>  
        public Result GetSchema(string xsdLocation,  
                                string xsdNamespace,  
                        out string xsdSchema)   
      {  
            xsdSchema = null;  
            return Result.Continue;  
        }  
```