---
title: "Limitations de l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limitations of, Siebel adapter
- Siebel adapter, limitations of
ms.assetid: fda63dd6-bad5-4f6d-8cc1-5855efb6f063
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9018c79e910c2bfac05f07466cbeeb79ea045ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-siebel-ebusiness-applications"></a>Limitations de l’adaptateur BizTalk pour Siebel eBusiness Applications
Les éléments suivants sont connus des limitations de la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]:  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas compatible avec l’adaptateur Microsoft BizTalk pour Siebel eBusiness Applications, la version précédente de l’adaptateur. La version actuelle de l’adaptateur ne prend pas en charge les envoyer et recevoir des messages qui ont des schémas générés à l’aide de la version antérieure de l’adaptateur.  
  
    > [!NOTE]
    >  Vous pouvez modifier les projets BizTalk pour les versions antérieures de l’adaptateur Siebel à utiliser le nouveau basé sur WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour plus d’informations, consultez [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur Siebel](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge les objets de flux de travail.  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne valide pas le format dans lequel un client passe une valeur de temps au système Siebel. Les clients de l’adaptateur doivent s’assurer que la valeur spécifiée pour un champ de date et d’heure respecte un format dans lequel le système Siebel attend.  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’effectue pas de validation de schéma. Par exemple, un champ de longueur 30 peut prendre les valeurs dont la longueur de 100, autorisée par le système Siebel. Il peut également entraîner une perte de données dans certains scénarios, car les données que le client insère via des objets métier peut-être pas nécessairement les données qui sont écrite dans la base de données. Les clients de l’adaptateur doivent valider explicitement l’entrée par rapport au schéma qui est visible par l’adaptateur. Toutefois, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne valide pas que tous les champs (pour les composants de l’entreprise) de requis ou arguments (pour les services d’entreprise) sont spécifiés.  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] attend les valeurs d’heure doit être spécifié dans le format Siebel standard, qui est HH : mm :. Les valeurs qui sont spécifiés dans un autre format génère une erreur, d’heure et la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] lève une `TargetSystemException`.  
  
-   Dans certains scénarios, l’application Siebel peut ou ne peut pas lever un message d’erreur. Par exemple, une opération de recherche à l’aide d’une expression peut lever une exception soit retourner zéro accords. En conséquence, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut lever un `TargetSystemException` ou obtenir un XML vide comme sortie.  
  
-   Lors de la récupération des données à partir du système Siebel en utilisant le modèle de service WCF, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne désérialise pas XMLs comportant des nœuds de plus de 65 536. Assurez-vous que le fichier de sortie XML possède des nœuds est inférieur ou égal à 65 536. Vous pouvez contourner cette limitation en modifiant le fichier app.config de votre application. Pour obtenir des instructions, consultez [dépannage des problèmes opérationnels avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-operational-issues-with-the-siebel-adapter.md).  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] récupère la longueur maximale d’un champ de la couche de composant métier, par opposition à la couche de base de données. Par conséquent, si vous essayez d’insérer une valeur conforme à la longueur maximale de la colonne de base de données, mais ce qui est supérieur à la longueur maximale du champ correspondant pour un composant d’entreprise, la valeur écrite dans la base de données peut être différente de celle que vous souhaitiez Pour entrer.  
  
-   Lors de l’exécution d’opérations par lots (Insert, Update et Delete), le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] génère une erreur si la première opération entraîne une erreur. Toutefois, si la première opération réussit et qu’une des opérations suivantes échoue, l’adaptateur ne lève pas d’une erreur, mais plutôt renvoie les ID des enregistrements qui correspondent aux réussite des opérations dans la sortie. Les clients de l’adaptateur doivent explicitement vérifier si toutes les opérations ont réussi.  
  
-   En raison de problèmes de délai d’attente un traitement par le client Siebel sous-jacent API, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.  
  
-   Considérez un scénario où l’utilisateur « A » génère les métadonnées d’une opération dans Siebel. Un autre utilisateur « B », avec des privilèges moindres que l’utilisateur « A », sera en mesure d’accéder aux métadonnées. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’effectue pas les vérifications pour confirmer que l’utilisateur « B » doit obtenir l’accès aux métadonnées. Toutefois, en raison de privilèges insuffisants utilisateur « B » ne peut pas être en mesure d’exécuter des opérations sur le système Siebel en utilisant les métadonnées.  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Pour chaque valeur de paramètre qui contient des caractères spéciaux, veillez à que remplacer les caractères spéciaux par les valeurs correspondantes, comme spécifié par les normes de codage URI.  
  
-   Lorsque vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], si les informations d’identification sur WCF-Custom envoie de port sont incorrectes, les messages de demande ne sont pas traités. Après avoir spécifié les informations d’identification correctes, le message est envoyé au système Siebel et une réponse est reçue. Toutefois, le message de réponse n’est pas disponible pour le port de sortie. Dans de tels scénarios, vous devrez peut-être redémarrer l’instance d’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)