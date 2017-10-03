---
title: "Comment activer ASP.NET 4.0 pour les Services Web publiés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58646ff2-77a3-49dc-8593-f6e41d85d4f3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68b8eef114828ad181e83ce0c7acd70a5545e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-aspnet-40-for-published-web-services"></a>Comment activer ASP.NET 4.0 pour les Services Web publiés
Définissez la version de ASP.Net dans IIS.

L’Assistant Publication de BizTalk Server Web Services s’appuie sur les fonctionnalités fournies avec ASP.NET, qui est inclus dans le .NET Framework. Les versions de ASP.Net sont incluses avec la version CLR .NET que vous choisissez. 

Cette rubrique montre comment modifier la version CLR .NET. 

## <a name="prerequisites"></a>Conditions préalables

IIS est inclus dans le **serveur Web (IIS)** rôle dans le système d’exploitation. Lorsque vous installez ce rôle, également sélectionner la version la plus récente de ASP.NET. 
  
## <a name="update-an-application-pool"></a>Mettre à jour un pool d’applications
  
1.  Ouvrez **Internet Information Services (IIS) Manager**:

    1. Dans **le Gestionnaire de serveur**, sélectionnez **outils**.
    2. Sélectionnez **Internet Information Services (IIS) Manager**.
  
2.  Développez le nom du serveur, puis sélectionnez **Pools d’applications**.  
  
3.  Sélectionnez le pool d’applications, puis ouvrez le **les paramètres de base**.  
  
4. Définir le **version .NET CLR** à la version plus récente, puis sélectionnez **OK** pour enregistrer vos modifications.  

> [!NOTE]
> Vous pouvez également modifier la version dans le fichier web.config.
 
## <a name="allow-the-aspnet-extension"></a>Autoriser l’extension ASP.Net
  
1.  Ouvrez **Internet Information Services (IIS) Manager**:

    1. Dans **le Gestionnaire de serveur**, sélectionnez **outils**.
    2. Sélectionnez **Internet Information Services (IIS) Manager**.
  
2.  Sélectionnez le nom du serveur, puis double-cliquez sur **Restrictions ISAPI et CGI**.  
  
3. Confirmer l’ASP.NET **autorisées** pour les versions 32 bits et 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la publication de Services Web](../core/planning-for-publishing-web-services2.md)