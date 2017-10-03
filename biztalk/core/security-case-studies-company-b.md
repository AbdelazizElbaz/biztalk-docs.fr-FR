---
title: "Études de cas de sécurité : La société B | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, examples
- security, architecture
- architecture, security
- security, case studies
ms.assetid: 48bbb347-919a-435e-b7b1-34a4c0e65e59
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef0e37d4acda263822a2cf06095f2c8fd9989afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-company-b"></a>Études de cas de sécurité : La société B
La société B est un éditeur de logiciels. Son modèle d'entreprise s'appuie sur des transactions électroniques entre des clients et des fournisseurs importants. Elle exploite une implémentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour ses transactions.  
  
 La société B utilise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour gérer les transactions et les communications entre les applications internes et externes. Elle communique avec environ 85 applications internes et 2300 partenaires commerciaux. Elle traite actuellement aux alentours de 2,5 millions de documents par mois et prévoit que ce chiffre atteindra 6 millions à la fin de l'année 2007.  
  
## <a name="potential-threats-and-security-concerns"></a>Menaces potentielles et problèmes de sécurité  
 La société B veut avoir l'assurance qu'elle reçoit et traite uniquement des messages provenant de sources authentifiées. Elle souhaite également s'assurer qu'elle puisse recevoir et récupérer des documents en toute sécurité en dehors de son réseau d'entreprise. Le pare-feu qui sépare le réseau d’entreprise de la société B à partir d’Internet uniquement vous permet de passer le trafic sur les ports 80 et 443. Le pare-feu rejette tout autre trafic.  
  
## <a name="security-architecture"></a>Architecture de la sécurité  
 L'architecture utilisée par la société B est représentée dans la figure suivante. Cette société utilise BizTalk Server comme un courtier de messages pour communiquer entre les applications internes mais également pour traiter, recevoir et envoyer des messages au format approprié en provenance ou à destination de ses fournisseurs et clients. Elle doit traiter des documents internes et externes dans plusieurs formats, y compris les fichiers plats et des documents XML.  
  
 **Figure 1 architecture de sécurité société B**  
  
 ![L’architecture de la société B](../core/media/bpi-cp-pc-company-b.gif "BPI_CP_PC_COMPANY_B")  
  
 Un pare-feu unique sépare d'Internet les ordinateurs d'entreprise de la société B. Cette société implémente une couche de sécurité supplémentaire en intégrant le protocole IPSec (Internet Protocol Security) aux communications entre l'intégralité de ses serveurs d'entreprise et les stations de travail résidant à l'intérieur du réseau d'entreprise. Le protocole IPSec permet de chiffrer toutes les communications au sein du domaine interne.  
  
 La société B utilise un serveur de partage de fichiers pour recevoir des fichiers plats. Celui-ci réside en dehors de son domaine et de son réseau d'entreprise. Un pare-feu sépare ce serveur du réseau d'entreprise. Les partenaires externes de la société B envoient leurs documents de fichier plat sur ce serveur de partage de fichiers par l'intermédiaire d'un pipeline PPTP (Point-to-Point Tunneling Protocol) chiffré. La société B protège l'accès à ce serveur au moyen de mots de passe partenaires qui expirent tous les 30 jours.  
  
 La société B a créé une application de déplacement de fichiers personnalisée qui récupère les documents de fichier plat sur le serveur de partage de fichiers et les envoie à BizTalk Server pour des traitements supplémentaires. Les applications internes de la société B utilisent également l'application de déplacement de fichiers personnalisée pour transmettre les fichiers plats à BizTalk Server. BizTalk Server transforme ensuite ces documents, puis il les envoie aux partenaires commerciaux de la société B.  
  
 Avant que BizTalk Server transforme les données des partenaires aux formats pris en charge par les applications internes, il vérifie puis valide la présence d'une entrée correspondant à l'expéditeur, au récepteur et au type de document. Si BizTalk Server reçoit un message dans lequel il n'existe aucune entrée pour l'expéditeur, le récepteur ou le type de document, il rejette le message. L'équipe des opérations au sein de la société B est alors chargée d'examiner le message. Les applications internes envoient des messages dans divers formats dont EDIFACT, fichier plat, XML et ANSI X12.  
  
 La société B reçoit également des documents via HTTPS en provenance de sources internes et externes. Les partenaires externes envoient leurs documents vers un serveur Web situé en dehors du réseau d'entreprise. Un pare-feu sépare ce serveur Web du réseau d'entreprise. L'application de déplacement de fichiers personnalisée récupère aussi les documents envoyés via HTTPS. La société B fait appel à un produit tiers pour chiffrer et signer les messages envoyés à ses partenaires commerciaux. Elle implémente un niveau de sécurité supplémentaire en réalisant un audit de nuit sur tous les serveurs afin de vérifier que les paramètres de sécurité sont corrects. Toutes les exceptions sont consignées à des fins d'analyse.  
  
## <a name="see-also"></a>Voir aussi  
 
 [Études de cas de sécurité pour les petites et moyennes entreprises](../core/security-case-studies-for-small-to-medium-sized-companies.md)   
 
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)