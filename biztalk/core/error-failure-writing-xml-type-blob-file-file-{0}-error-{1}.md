---
title: "Erreur : Échec de l’écriture du fichier de l’objet Blob de Type XML (&lt;file:---{0}&gt;). Erreur : {{1} de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb787db4-0919-4e1b-bfe1-ba0e19a08881
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d76ff1a81045d3b764a6a26112a1efd74b284674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---failure-writing-xml-type-blob-file-ltfile---0gt-error-1"></a>Erreur : Échec de l’écriture du fichier de l’objet Blob de Type XML (&lt;file:---{0}&gt;). Erreur : {{1}
**Code d’erreur**  
  
 btm1062  
  
 **Explication**  
  
 Ceci se produit lorsque le compilateur du mappeur n'est pas en mesure de créer le fichier blob xml dans l'emplacement spécifié par la tâche de génération.  
  
 **Action de l’utilisateur**  
  
 Vérifiez le message d’erreur inclus dans le message (erreur {1})i. S’il est une exception non autorisée, vous pouvez avoir pas d’autorisation en écriture pour le dossier de sortie du projet.