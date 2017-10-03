---
title: "Propriétés du Transport de réception du paramètre TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transport properties, setting for receive ports
- setting transport properties, receive
ms.assetid: 56e0a51a-6505-43bf-a48b-de35f4b114df
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06ff1b3a11d6b95c2fb784e969363433dec3dc28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-tibco-rendezvous-receive-transport-properties"></a>Configuration des propriétés du transport de réception TIBCO Rendezvous
Lorsque vous configurez l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous pour écouter les messages, vous spécifiez les noms d'objet à écouter. Il s'agit de la seule propriété requise.  
  
 Cette procédure permet de spécifier les propriétés.  
  
### <a name="to-specify-tibco-rendezvous-transport-properties"></a>Pour spécifier les propriétés de transport TIBCO Rendezvous  
  
1.  Dans la boîte de dialogue Propriétés du Transport TIBCO Rendezvous, développez **propriétés obligatoires de l’adaptateur**, entrez la **nom d’objet Rendezvous**.  
  
     Il s'agit du nom de l'objet (les caractères génériques de Rendezvous sont autorisés) que l'adaptateur écoute. Dans le scénario de déploiement le plus simple, ceci est la seule propriété requise.  
  
     ![](../core/media/sadp-tibcorecvtranspropertiess.gif "SAdp_TIBCORecvTransPropertiess")  
  
2.  Dans le **paramètres de l’écouteur certifié**, fournissez le nom réutilisable et le nom du fichier de comptabilité si vous voulez une messagerie certifiée.  
  
     Ce champ est obligatoire si vous définissez une file d'attente distribuée. Si une messagerie certifiée n'est pas nécessaire, laissez ces entrées vides. Le nom du fichier de comptabilité et le nom réutilisable doivent être uniques parmi tous les ports définis sur cet hôte et les autres programmes TIBCO Rendezvous s'exécutant sur cet hôte. Si tel n'est pas le cas, l'interface utilisateur ne le détecte pas mais une erreur est interceptée et consignée au moment de l'exécution.  
  
3.  Dans le **les paramètres de file d’attente distribuée**, si la file d’attente distribuée n’est pas nécessaire, ne modifiez pas les entrées.  
  
     Les valeurs suivantes sont utilisées avec un groupe BizTalk Server. L'adaptateur BizTalk pour TIBCO Rendezvous utilise ces valeurs dans les appels d'API à TIBCO RV.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du fichier de comptabilité**|Nom du fichier de comptabilité de l'écouteur certifié (ou du membre du groupe). Valeur par défaut est Null.<br /><br /> Si aucune valeur n'est spécifiée, un fichier de comptabilité en mémoire est utilisé.|  
    |**Nom réutilisable**|Nom réutilisable de l'écouteur certifié (ou du membre du groupe). Valeur par défaut est Null.<br /><br /> Un nom réutilisable est requis pour garantir un processus en cours de redémarrage. Si aucune valeur n'est spécifiée, un nom (non réutilisable) généré est utilisé.|  
  
     Les files d'attente distribuées sont utiles en cas de déploiement d'un emplacement de réception TIBCO Rendezvous dans un groupe BizTalk Server. Dans ce cas, entrez les valeurs d'intervalle et de stratégie souhaitées. Les intervalles d'activation et Heart Beat sont fournis en l'état à TIBCO Rendezvous. Comme les intervalles doivent être identiques parmi tous les participants d'une file d'attente distribuée, les valeurs sont entrées une fois seulement. Avec les stratégies, il se peut que les valeurs soient différentes sur chaque hôte. Toutes les valeurs de stratégie suivent la même syntaxe : paires hôte/valeur séparées par un deux-points (:) séparées par un point-virgule (;).  
  
     Par exemple, **host1:10 ; host2:20 ; host3:30**  
  
     Le nom de l'hôte doit être un nom d'hôte DNS valide ou une adresse IP. Pour chacune de ces stratégies, l'adaptateur trouve la valeur associée à son hôte et l'utilise avec l'API TIBCO Rendezvous.  
  
     Si les valeurs doivent être identiques sur tous les ordinateurs, vous pouvez enteOn le Tibr une valeur simple au lieu de la liste de paires nom-valeur (par exemple, **20**).  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Intervalle d’activation**|Planificateur Stratégie de poids utilisé pour cette file d'attente distribuée. Il s'agit de l'intervalle sans message Heart Beat du planificateur, après lequel TIBCO RV active un nouveau planificateur. La valeur par défaut est 20 secondes.|  
    |**Intervalle de pulsations**|Intervalle Heart Beat utilisé dans cette file d'attente distribuée. Il est utilisé avec le paramètre Groupe BizTalk Server. L'adaptateur BizTalk pour TIBCO Rendezvous utilise ces valeurs dans les appels d'API à TIBCO RV. La valeur est utilisée par l'instance de l'adaptateur qui est le planificateur actif pour le groupe et diffuse les messages Heart Beat à cet intervalle (en secondes). Valeur par défaut est 10.|  
    |**Planificateur stratégie de poids**|Par défaut (valeur nulle), tous les membres d'un groupe ont la même chance de devenir planificateur. Une liste de valeurs de paire hôte-poids prévoit une stratégie de poids différente. Valeur par défaut est Null.|  
    |**Stratégie de la capacité de travail**|Stratégie de capacité de travail utilisée pour cette file d'attente distribuée. Cette valeur indique le nombre de tâches simultanées qu'un membre du groupe peut gérer. Si aucune valeur n'est spécifiée, la valeur par défaut est 1. Une liste de valeurs de paire hôte-capacité prévoit une stratégie de capacité différente.|  
    |**Stratégie de poids de travail**|Stratégie de poids de travail utilisée pour cette file d'attente distribuée. Cette valeur fournit une valeur de poids pour aider TIBCO à attribuer des tâches dans une file d'attente distribuée. En commençant par le poids le plus élevé, des tâches sont attribuées aux employés disponibles. Valeur par défaut est 1.|  
  
4.  Développez **paramètres généraux** et entrez les informations requises pour la connexion au serveur TIBCO Rendezvous.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Substitution de caractères génériques annexe**|Spécifiez un texte de substitution des caractères génériques. Les noms d'objet qu'un emplacement de réception écoute sont utilisés pour générer l'espace de noms cible XML dans les messages obtenus. Par défaut, l'adaptateur remplace tout caractère générique « > » par le texte GTWILDCARD dans les messages générés. Vous pouvez spécifier un caractère générique différent dans ce champ.|  
    |**Numéro de Page de codes**|Identifie la page de code utilisée par l'expéditeur du message pour coder les chaînes contenues dans les messages entrants. Valeur par défaut est 65001. (L'adaptateur ne peut pas avoir les mêmes objets de message générés à partir de deux environnements de page de code différents.)|  
    |**Substitution de caractères génériques d’élément**|Spécifiez un texte de substitution génériques différents les noms d’objet qu’un emplacement de réception écoute sont utilisés pour générer l’espace de noms cible XML dans les messages obtenus. Par défaut, l'adaptateur remplace tout caractère générique « * » par le texte STARWILDCARD dans les messages générés. Vous pouvez spécifier un caractère générique différent dans ce champ.|  
    |**Nom de file d’attente d’événement**|Spécifiez un nom à utiliser lors de la création de l'objet File d'attente Rendezvous. Il est fourni pour des raisons de commodité car les messages du journal associés affichent le nom de cette file d'attente. Valeur par défaut est vide.|  
    |**Filter**|Lorsque vous spécifiez des caractères génériques dans les noms d'objet à écouter, l'orchestration cible risque de ne s'intéresser qu'à un sous-ensemble de l'ensemble potentiellement très large d'objets qu'elle pourrait concerner. Pour réduire l'impact sur BizTalk Server et l'accès associé aux bases de données, vous pouvez continuer à spécifier les messages à envoyer à BizTalk Server. Cette entrée contient une liste séparée par un point-virgule des noms d'objet (sans caractère générique autorisé). Tout message correspondant à un nom d'objet spécifié avec un caractère générique mais dont le nom d'objet ne figure pas dans cette liste est filtré (non envoyé à BizTalk Server). La logique du filtre peut être inversée en ajoutant un caractère « ! » au début de la valeur de filtre. Par défaut, aucune valeur n'est spécifiée (aucun filtre).|  
    |**Mapper les types non pris en charge à la chaîne**|Les types non pris en charge génèrent une erreur ou sont mappés à la chaîne. Utilisable si l'adaptateur est utilisé avec une version plus récente de TIBCO Rendezvous où de nouveaux types auraient été ajoutés.|  
    |**Membre du groupe BizTalk**|Si défini sur True, les paramètres de file d'attente distribuée (qui font référence au nœud Paramètres de file d'attente distribuée) et les paramètres d'écouteur certifié (qui font référence au nœud Paramètres de l'écouteur certifié) doivent être définis. La valeur par défaut est FALSE.|  
    |**Chemin d'accès**|Défini pour pointer sur les binaires TIBCO Rendezvous si cette information n'est pas déjà dans la variable d'environnement PATH.|  
    |**Conserver l’ordre**|L'adaptateur distribue les messages entrants à BizTalk Server dans l'ordre de leur réception (par exemple, à l'aide d'un simple thread de distribution). Notez que si les paramètres de messagerie certifiée ne sont pas définis, cela ne signifie pas que l'adaptateur reçoit les messages dans l'ordre de leur envoi (en faisant référence à une seule source).|  
    |**Identificateur d’emplacement de réception**|Nom de l'emplacement de réception.|  
    |**Réservé**|Champ réservé à un usage particulier.|  
  
5.  Développez le **Transport Rendezvous**et entrez les informations requises pour la communication entre les programmes et démons TIBCO Rendezvous.  
  
     Le **Transport (réseau, démon, Service)** spécifie comment les démons TIBCO Rendezvous échangent des messages. Ces paramètres sont envoyés en l'état à l'API TIBCO Rendezvous. L'utilisation des valeurs par défaut (vides) revient à utiliser la stratégie de communication par défaut.  
  
     Un transport TIBCO Rendezvous définit l'étendue de remise, c'est-à-dire l'ensemble des destinations possibles auxquelles envoyer le message. Cet ensemble de propriétés définit un transport.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**Démon**|Tapez l'identificateur numérique du paramètre Démon du transport Rendezvous.|  
    |**Réseau**|Tapez le nom du paramètre Réseau Rendezvous.|  
    |**Nom de service**`e`|Tapez le nom du service du transport Rendezvous.|  
  
6.  Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).  
  
     Vous pouvez utiliser deux méthodes pour accéder au système TIBCO Rendezvous. Vous pouvez utiliser les informations d'identification (paramètres Nom d'utilisateur et Mot de passe) ou l'authentification unique.  
  
    1.  Sélectionnez **Oui** dans les **utiliser SSO** à utiliser l’authentification unique.  
  
        > [!NOTE]
        >  Consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on5.md) pour plus d’informations sur la façon de configurer l’authentification unique.  
  
    2.  Sélectionnez une application associée dans la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO Rendezvous. L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise les informations d'identification d'un utilisateur de l'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).  
  
7.  Après avoir entré toutes les informations requises, cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
     Vous devez définir les paramètres de connexion pour l'adaptateur BizTalk pour TIBCO Rendezvous afin de recevoir les messages TIBCO Rendezvous.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaires de réception création TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)