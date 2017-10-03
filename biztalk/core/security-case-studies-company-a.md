---
title: "Études de cas de sécurité : La société A | Documents Microsoft"
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
ms.assetid: 9417ecf9-e340-479f-b120-552c62f3b189
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1f48edfc2ab2228d910a0729025fd7b4da117f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-company-a"></a>Études de cas de sécurité : La société A
La société A est un fournisseur important de matériel et services destinés au secteur industriel. Son modèle d'entreprise s'appuie sur des transactions électroniques entre des clients et des fournisseurs importants. La société A utilise une application Microsoft BizTalk pour gérer les transactions et la communication entre les environnements interne et externe.  
  
## <a name="potential-threats-and-security-concerns"></a>Menaces potentielles et problèmes de sécurité  
 La société A veut avoir l'assurance qu'elle traite uniquement des messages provenant de sources authentifiées. Certains documents traités par BizTalk Server peuvent contenir des informations sensibles, telles que des données personnelles et financières. La société A vérifie les messages entrants à l'aide d'API de chiffrement personnalisées. Elle a également développé son architecture physique pour gérer ses besoins en matière de sécurité.  
  
 La société A utilise le protocole FTP (File Transfer Protocol) pour une partie du trafic de ses messages. Bien que le protocole FTP ne soit pas sécurisé, la société A accepte les risques associés à son utilisation car elle dispose de plusieurs pare-feu pour sécuriser ses applications connectées à l'extérieur. Comme la société A reçoit certaines données entrantes via HTTPS, elle est potentiellement exposée aux attaques par déni de service provenant de sources externes. Si ce type d'attaque se produit, la société a mis en place des mécanismes capables d'alerter les responsables concernés immédiatement.  
  
## <a name="security-architecture"></a>Architecture de la sécurité  
 L'architecture de sécurité utilisée par la société A est représentée dans la figure suivante. Notez qu'elle a segmenté son environnement à l'aide de pare-feu pour protéger son application frontale, ses serveurs de contenu, sa base de données principale, ses serveurs de logique d'entreprise et son infrastructure de messages sortants.  
  
 **Figure 1 architecture de sécurité de la société A**  
  
 ![Une architecture de sécurité de l’entreprise](../core/media/airproductsbiztalkinfrastructure.gif "AirProductsBizTalkInfrastructure")  
  
 La société A a défini deux méthodes principales pour l'envoi et la réception d'informations via BizTalk Server. La première méthode utilise le protocole FTP. La société A prend en charge les transactions EDI à l'aide d'un fournisseur de service de conversion tiers pour communiquer avec ses fournisseurs et partenaires. Ce fournisseur de service de conversion tiers gère les commandes entrantes et sortantes que BizTalk Server doit traiter au format EDI.  
  
 La seconde méthode utilisée par la société A utilise le protocole HTTPS. La société A fait également appel à un fournisseur de service tiers qui lui sert de hub pour ses activités et simplifie l'achat et la vente des produits qu'elle vend et utilise.  
  
## <a name="secure-digital-certificates"></a>Certificats numériques sécurisés  
 La société A implémente ses propres certificats numériques sécurisés. Elle gère un nombre restreint de certificats. Comme elle fait appel à un fournisseur de service tiers, le problème des certificats numériques la concerne moins. La société A a conscience que les certificats numériques constituent un aspect plus important pour le fournisseur de service, car celui-ci interagit avec plusieurs organismes.  
  
## <a name="see-also"></a>Voir aussi  
 [Études de cas de sécurité pour les petites et moyennes entreprises](../core/security-case-studies-for-small-to-medium-sized-companies.md)    
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)