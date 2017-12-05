---
title: "Liste de vérification : Configuration d’Internet Information Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 186f82c0-bd50-4c79-a403-8b0d91cc68d6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c2c0c97cb70dca268273d9ed5855f72372a2ca
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="checklist-configuring-internet-information-services"></a>Liste de vérification : Configuration d’Internet Information Services
Cette rubrique répertorie les étapes à suivre lors de la préparation des Internet Information Services (IIS) pour une utilisation dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Configurer IIS pour publier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web et les services WCF|-Découvrez [« Activation des Services Web »](http://go.microsoft.com/fwlink/?LinkId=153335) (http://go.microsoft.com/fwlink/?LinkId=153335) dans la documentation de BizTalk Server.<br />-Découvrez [« Configuration IIS pour les adaptateurs WCF isolés de réception »](http://go.microsoft.com/fwlink/?LinkId=202825)(http://go.microsoft.com/fwlink/?LinkId=202825) dans la documentation de BizTalk Server.|  
|Vérifiez que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web et les services WCF fonctionnent correctement.|-Découvrez [« Test de Services Web publiés »](http://go.microsoft.com/fwlink/?LinkId=153336) (http://go.microsoft.com/fwlink/?LinkId=153336) dans la documentation de BizTalk Server.<br />-Découvrez [« Comment pour créer un .NET Application à Test un WCF Service publiée avec le Service Assistant Publication WCF BizTalk »](http://go.microsoft.com/fwlink/?LinkId=202830) (http://go.microsoft.com/fwlink/?LinkId=202830) dans la documentation de BizTalk Server.|  
|Verrouiller [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web :<br /><br /> -Mettez hors tension le commutateur de débogage dans le fichier web.config ou machine.config.<br />-Configurer afin que la publication est le seul verbe autorisé.|-Consultez l’Article de la Base de connaissances Microsoft 815145, [« Comment : verrouiller une Application Web ASP.NET ou Service Web «](http://go.microsoft.com/fwlink/?LinkId=153337) (http://go.microsoft.com/fwlink/?LinkId=153337).<br />-Découvrez [« ASP.NET règle boîte de dialogue Modifier »](http://go.microsoft.com/fwlink/?LinkID=64566) (http://go.microsoft.com/fwlink/?LinkID=64566) dans la documentation .NET Framework 2.0.|  
|Configurez à l’aide d’équilibrage de charge réseau (ou un autre équilibreur de charge) pour équilibrer la charge entre les services Web BizTalk Server et les services WCF d’équilibrage de charge.|-   **Pour Windows Server 2008**: consultez [« Guide de déploiement de l’équilibrage de charge réseau »](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139).<br />-   **Pour Windows Server 2003**: consultez [« équilibrage de la charge réseau : meilleures pratiques de Configuration pour Windows 2000 et Windows Server 2003 »](http://go.microsoft.com/fwlink/?LinkID=69529) (http://go.microsoft.com/fwlink/?LinkID=69529).|  
|Modifier les paramètres IIS et ASP.NET pour le paramétrage des services Web. **Remarque :** ASP.NET 2.0 comprend le réglage automatique, par conséquent, de modifier ces paramètres ne doit pas nécessaire pour le fichier web.config de sites Web ASP.NET 2.0 où la configuration automatique est activée dans le \<processModel\> section. « autoConfig = true » est le paramètre par défaut.|Passez en revue les « paramètres ASP.NET pouvant affecter les performances d’adaptateur HTTP ou SOAP » section de la rubrique [« Configuration de paramètres qui affectent performances de l’adaptateur »](http://go.microsoft.com/fwlink/?LinkId=153338) (http://go.microsoft.com/fwlink/?LinkId=153338) dans la documentation de BizTalk Server.|  
|Implémenter une approche pour la publication [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web et les services WCF.|-Découvrez [les Services Web sur Internet et les Services WCF de publication](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md).<br />-Découvrez [« Publication des Services WCF »](http://go.microsoft.com/fwlink/?LinkId=202827) (http://go.microsoft.com/fwlink/?LinkId=202827) dans la documentation de BizTalk Server.|  
|Suivez les meilleures pratiques pour optimiser les performances d’IIS.|Consultez [« Principales façons de dix de pompe les performances d’IIS »](http://go.microsoft.com/fwlink/?LinkId=109107) (http://go.microsoft.com/fwlink/?LinkId=109107).|  
|Suivez les meilleures pratiques pour l’écriture d’applications web pour IIS hautes performances.|Consultez [« 10 conseils pour l’écriture de hautes performances des Applications Web »](http://go.microsoft.com/fwlink/?LinkId=98290) (http://go.microsoft.com/fwlink/?LinkId=98290).|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Publication des services web et des services WCF accessibles sur Internet](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)