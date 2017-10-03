---
title: "Vérification du déploiement Setup1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLASSPATH, verifying
- deployment, verifying setup
ms.assetid: 6c719e4c-9a61-480f-a4e4-0a1c518d1364
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5799d164dc2470236c3ab0286e38d19986a4d5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="verifying-the-deployment-setup"></a>Vérification de la configuration du déploiement
Avant d'utiliser le serveur BizTalk pour importer un fichier de liaison, vous devez vérifier les éléments suivants se réalisent :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards EnterpriseOne. Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les mots de passe du système JD Edwards EnterpriseOne, si cette option a été définie dans la configuration, sont enregistrés en tant que ***** dans le fichier de liaison. Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations4.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies3.md)