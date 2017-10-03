---
title: "Fonctionnement de l’exemple de Service de gestion des exceptions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d095752-e212-42bf-9559-efa14d2ad09c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eac3a9ff96025f5248c0434a69c38eb01a704488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-exception-handling-service-sample-works"></a>Fonctionnement de l’exemple de Service de gestion des exceptions
L’exemple de Service de gestion des exceptions est une application Windows Forms .NET standard qui contient un proxy de service généré pour le service de gestion des exceptions. L’application se compose d’un formulaire unique avec un seul bouton **générer une Exception**. Lorsque vous cliquez sur ce bouton, une instance de la **FaultMessage** classe est générée. Le **FaultMessage** est une classe qui a été générée par Microsoft Visual Studio est basée sur la Description langage WSDL (Web Services) fournies par le service Web de gestion des exceptions. Les propriétés de cette instance sont remplies avec les valeurs par défaut qui simulent une erreur qui se produisent dans une application externe avant que les propriétés sont passées en tant que paramètres à la **SubmitFault** du site Web la gestion des exceptions (méthode) service.  
  
 Pour plus d’informations sur le fonctionne du service Web de gestion des exceptions, consultez [le Service de Web Gestion des exceptions](../esb-toolkit/the-exception-handling-web-service.md).