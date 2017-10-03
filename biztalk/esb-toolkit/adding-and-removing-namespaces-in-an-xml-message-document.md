---
title: Ajout et suppression des espaces de noms dans un document XML de Document Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf2f209-13b9-42e0-b0f2-b53ec705e84b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3bb3b28504f92164aca1f66902546f1e04a2290
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-and-removing-namespaces-in-an-xml-message-document"></a>Ajout et suppression des espaces de noms dans un Document XML du Message
Dans ce cas de figure, le composant Namespace fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] ajoute des espaces de noms, ou supprime les espaces de noms à partir des documents et des messages, comme illustré dans la Figure 1. Cela empêche les conflits d’espace de noms ou les erreurs liées lorsque les documents utilisent des espaces de noms par défaut.  
  
 ![Ajout de suppression des espaces de noms](../esb-toolkit/media/ch3-addingremovingnamespaces.gif "Ch3-AddingRemovingNamespaces")  
  
 **Figure 1**  
  
 **Ajout et suppression des espaces de noms XML document et de message**  
  
 L’exemple de composant de Namespace inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment utiliser le composant pour insérer et supprimer des espaces de noms dans un document dans le cadre de l’envoi et le processus de réception.  
  
 Pour plus d’informations, consultez [installer et exécuter l’exemple de composant Namespace](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).