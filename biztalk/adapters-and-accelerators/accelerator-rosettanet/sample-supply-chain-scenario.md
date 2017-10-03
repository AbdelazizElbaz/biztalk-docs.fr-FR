---
title: "Exemple de scénario de chaîne d’approvisionnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- examples, supply chains
ms.assetid: 1837a2c8-b1d4-4e1f-a196-a48b13b22662
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e305021e5b1206cc46ba40c2d2c4cd098c6c6e06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-supply-chain-scenario"></a>Exemple de scénario de chaîne logistique
Un processus plus fondamentales dans la chaîne d’approvisionnement de haute technologie est l’échange de messages de demande et de réponse de bon de commande. Un acheteur émet un bon de commande et un fournisseur accuse réception, au niveau de la ligne, ils acceptent ou rejettent l’ordre, ou si la commande est en attente.  
  
 Cette rubrique décrit un exemple de scénario de deux partenaires commerciaux qui échangent des messages de bon de commande et montre comment intégration et automatisation améliorent le processus.  
  
## <a name="the-players"></a>Les lecteurs  
 L’acheteur dans cet exemple de scénario est un fabricant de la haute technologie volumineux. Ils utilisent actuellement un système EDI pour échanger des données automatisée. Avec des fournisseurs qui n’utilisent pas EDI, ils s’appuient sur le téléphone, télécopie, envoyer par courrier électronique avec des feuilles de calcul et des applications Web. Même avec ces fournisseurs qui n’utilisent pas EDI, ils ont une capacité limitée à intégrer leurs communications de partenariat commercial de leur système ERP de back-end. Après avoir reçu des commandes et des informations via EDI, ils doivent manuellement RE-key ces commandes dans leur système ERP. Ils souhaitent améliorer leurs processus existants de la chaîne d’approvisionnement en automatisant la demande, l’inventaire, d’achat et la création de rapports avec leurs partenaires commerciaux. Ils ont besoin d’un système de se connecter avec leurs fournisseurs et les clients via Internet qui s’intègre également directement avec leurs applications line of business (LOB) existantes.  
  
 Le vendeur est un fournisseur de taille moyenne de circuits à hautes performances (ICs). Actuellement communiquer avec leurs partenaires commerciaux à l’aide de téléphone, de télécopie, elles envoyer par courrier électronique avec joint [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] des feuilles de calcul, FTP et Web applications. Ils n’utilisent pas l’EDI. Interagit avec chaque partenaire commercial est différents, selon les besoins du client et leurs technologies. Ils souhaitent optimiser leurs processus d’entreprise pour réduire les coûts de transaction, améliorer la satisfaction client et un avantage concurrentiel.  
  
## <a name="the-present-business-process"></a>Le présent processus d’entreprise  
 Sans une solution intégrée, le processus de bon de commande pour le fabricant et le fournisseur fonctionne comme suit :  
  
1.  Un client du fabricant de matériel de haute technologie envoie une commande au fabricant via un site Web.  
  
2.  En réponse à la commande d’origine, un employé du constructeur crée une demande de bon de commande dans leur application ERP de cœur de métier pour le fournisseur de configuration initiale.  
  
3.  La demande de bon de commande traverse les différentes parties de la société de fabrication qui ont à enregistrer, traiter, passez en revue et autoriser la demande de bon de commande. Ce traitement et le routage sont une combinaison de processus automatisés pour les utilisateurs du système ERP et des processus manuels, comme le courrier électronique avec un joint [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul.  
  
4.  Un employé crée une demande de bon de commande dans le courrier électronique et l’envoie au fournisseur. Un nombre d’autres employés de communication par courrier électronique, télécopie ou EDI à d’autres fournisseurs Répétez ce processus. Différents services utilisent des processus différents. Avec ces fournisseurs qui utilisent l’EDI, un employé du fabricant doit toujours créer un message de manuellement à partir du système ERP.  
  
5.  Un employé au fournisseur reçoit le message et ensuite manuellement clés dans leur système ERP, modification du format des données. Par courrier électronique, l’employé notifie les autres employés de la demande.  
  
6.  Les autres employés analyser la requête. Si nécessaire, elles signalent leurs propres fournisseurs de parties de la nécessité pour les parties. Selon le fournisseur, elles utilisent les téléphoniques, télécopie, courrier électronique ou FTP pour avertir leurs fournisseurs.  
  
7.  Après consultation avec leurs services et les fournisseurs, chaque employé accepte ou rejette de chaque produit facturation, puis confirme ou rejette le bon de commande et indique qu’il est en attente. Ils effectuent ces tâches dans le système ERP.  
  
8.  Un employé du fournisseur crée une réponse de bon de commande dans le courrier électronique, confirmation ou de rejet de chaque élément de ligne de la demande, ou la création d’un message indiquant que le bon de commande est en attente. L’employé du fournisseur envoie le message de réponse au fabricant. Si une ligne est en attente, ils seront ultérieurement créer un autre message qui indique si l’élément en attente est accepté ou rejeté.  
  
9. Un employé du fabricant reçoit la réponse de bon de commande. Ils entrent de nouveau l’ordre dans leur système ERP de back-end.  
  
10. Un autre employé analyse la confirmation de bon de commande et crée ensuite une réponse au client d’origine, confirmation de la commande. Ils envoient cette réponse par courrier électronique.  
  
## <a name="the-rosettanet-solution"></a>La Solution RosettaNet  
 Microsoft BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] automatiser et normaliser le processus de demande et de réponse de bon de commande. À l’aide d’un système intégré réduit la quantité de la quantité de papier, la gestion et l’utilisation de machines de téléphones et de télécopie, une intervention manuelle. La plupart des processus sont automatisées transactions entre les ordinateurs de serveur intégré. Lorsque les employés doivent effectuer manuellement une opération, ils le font généralement sur des systèmes ERP de back-end. La figure suivante illustre le système intégré.  
  
 ![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-integrated-supply-chain-scenario.gif "RN3_Integrated_Supply_Chain_Scenario")  
  
 Dans ce scénario, un système intégré modifie les processus suivants :  
  
-   Une connexion de Framework RNIF (RosettaNet Implementation) remplace les interactions manuelles routines entre le fabricant et le fournisseur de configuration initiale. Le système automatiquement envoie et reçoit des messages, achemine les données vers les systèmes back-end et reconnaît et répond aux messages. Le fabricant et le fournisseur à utiliser [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pour implémenter la connexion RNIF.  
  
-   Une connexion RNIF remplace la connexion EDI entre le fabricant, le fournisseur IC et autres partenaires commerciaux. Ainsi, les données d’itinéraire intégration système automatiquement pour les systèmes back-end des partenaires commerciaux. Certaines des échanges partenaires utilisez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pour implémenter la connexion RNIF ; d’autres utilisent une autre solution compatible avec RosettaNet.  
  
-   Les partenaires plus petits qui n’ont pas d’une solution compatible avec RosettaNet, le fabricant et le fournisseur IC créent des services Web accessibles par le partenaire avec un navigateur Web. Le service Web utilise une connexion RNIF standard pour communiquer avec le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système sur le fabricant ou le fournisseur de configuration initiale.  
  
-   Les messages échangés par les fabricants et fournisseurs suivent des schémas qui sont conformes aux standard RosettaNet PIP (PIP). Ces schémas remplacent les formats utilisés dans EDI et FTP. Tous les partenaires commerciaux utilisent les mêmes schémas ; ils n’ont pas à mapper les données entre les messages.  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]valide automatiquement tous les messages par rapport aux schémas, le risque d’erreurs de données.  
  
-   Les administrateurs peuvent intervenir sur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] serveurs à l’aide des outils d’administration de logiciels. Décideurs d’entreprise sur les ordinateurs clients peuvent utiliser les outils de surveillance de l’entreprise hébergés dans les applications Microsoft Office ou les outils. Ces processus efficace que le système d’exploitation de manière efficace et fournissent une visibilité plus sur la manière dont le système et la manière dont l’entreprise, est en cours d’exécution.  
  
### <a name="message-flow"></a>Flux de messages  
 Le processus d’entreprise inclut maintenant les étapes suivantes :  
  
1.  Un client du fabricant de matériel de haute technologie envoie une commande au fabricant via un site Web.  
  
2.  En réponse à la commande d’origine, un employé du fabricant génère une demande de bon de commande sur l’ordre de l’entreprise et système de gestion des stocks. Cette application métier est un système ERP avec une interface utilisateur basée sur le Web.  
  
3.  Le système envoie à la demande de bon de commande, toujours dans le format natif du système ERP, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]génère automatiquement un message de demande de bon de commande conformes au PIP 3 a 4 défini par l’organisation RosettaNet. Cette demande de bon de commande est au format XML. Le PIP définit le contenu du message.  
  
    > [!NOTE]
    >  Le PIP 3 a 4 permet de s’assurer que toutes les demandes de bon de commande et les réponses sont identiques dans le formulaire. Ce processus PIP fait partie d’une collection de PIP défini par RosettaNet qui forment un système de messagerie complète, interconnecté. Par exemple, avant d’envoyer le message 3 a 4, l’acheteur peut rechercher des prix et disponibilité (PIP 3A2), demande un guillemet (PIP 3A1), ou transférer leur panier d’achat (PIP 3A3). Après l’envoi de la demande de bon de commande, l’acheteur peut modifier l’ordre d’achat (3 a 8 PIP), annuler le bon de commande (PIP 3A9), de requête pour l’état du bon de commande (PIP 3A5) ou distribuer l’état du bon de commande (PIP 3A6). L’organisation RosettaNet standard tous ces messages.  
  
5.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]encapsule le message de demande (nommé le contenu de service) avec des en-têtes RNIF qui vous permettent de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] transmettre le message via Internet à un autre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ordinateur sur le site du fournisseur. RNIF définit la manière dont les partenaires échangent des messages via Internet.  
  
6.  Le fabricant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système envoie la demande de bon de commande pour le fournisseur de IC [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système.  
  
7.  Du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système de N reçoit la demande de bon de commande. S’il s’agissait d’une demande d’action unique (un sans réponse correspondante), du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système renvoie un message de signal qui accuse réception du message. Toutefois, comme il s’agit d’un double action, le fournisseur du message [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système renvoie un message de signal d’accusé de réception reçu suivi d’un message de réponse est également.  
  
8.  Du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système supprime les en-têtes RNIF du message de demande de bon de commande, traite le contenu du message du service et achemine ensuite la demande au système ERP du fournisseur.  
  
9. Les employés du fournisseur fonctionnent dans le système ERP pour traiter la commande. S’ils ont envoyer des messages à leurs propres fournisseurs de parties, pour cela, ils utilisent la même BizTalk et [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système. Le service informatique peut personnaliser le système pour répondre au fabricant automatiquement.  
  
10. Un employé utilise le système ERP du fournisseur pour générer un message de réponse de bon de commande, puis achemine le message de réponse du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système.  
  
11. Du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système génère un message de réponse de bon de commande 3 a 4 PIP, encapsule le contenu du message de réponse du service dans les en-têtes RNIF, puis envoie la réponse de bon de commande pour le fabricant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système.  
  
12. Le fabricant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système reçoit la réponse de bon de commande, puis envoie un message d’accusé de réception à du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. Du fournisseur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] système achemine l’accusé de réception au système ERP du fournisseur.  
  
13. Le fabricant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] supprime les en-têtes RNIF du message de réponse, traite le contenu du service, puis achemine la réponse de bon de commande à l’application ERP du fabricant.  
  
14. Un employé du fabricant analyse tous les messages de confirmation de bon de commande et crée ensuite une réponse au client d’origine, confirmation de la commande. L’employé envoie ensuite cette réponse par courrier électronique.  
  
## <a name="advantages-of-the-btarn-solution"></a>Avantages de la Solution BTARN  
 BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] automatiser la plupart des aspects du processus de demande et de réponse de bon de commande. Pour cela, ils non seulement pour le fabricant et le fournisseur de configuration initiale, mais également pour tous les autres partenaires commerciaux qui ont adopté compatible avec RosettaNet solutions dans le cadre de la gestion de la chaîne d’approvisionnement.  
  
 Un système d’intégration réduit la quantité d’intervention manuelle et la quantité de gestion du papier. La plupart des processus impliquant automatisés d’interactions entre les ordinateurs de serveur intégré. Le fabricant et le fournisseur IC présentent un degré élevé de contrôle et la visibilité dans leurs processus. Ils automatiquement recevoir les accusés de réception et peuvent conserver la preuve de non répudiation.  
  
 Le système automatisés à l’aide [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] permet le fabricant et le fournisseur effectuer les opérations suivantes :  
  
-   Réduire les durées de cycle de traitement des commandes  
  
-   Réduire les incertitudes pouvant affecter le processus et augmenter la fiabilité du processus  
  
-   Réduire le temps de traitement et de temps de réponse de devis  
  
-   Réduire le temps manuellement réorganiser plus d’informations, obtention d’informations manquantes ou corriger les erreurs  
  
-   Offre une visibilité et activer l’analyse du processus et le suivi des messages  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server résout les besoins de l’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [La nécessité d’intégration de partenaires commerciaux](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md)   
 [Le défi de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md)   
 [La Solution de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md)   
 [Exemple de scénario basé sur un concentrateur](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md)