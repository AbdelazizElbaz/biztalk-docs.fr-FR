---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 1a32564f9e0e9e81624b39ab0ba156e76b109497
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="setting-tibco-enterprise-message-service-transport-properties-for-the-receive-port"></a>Configuration des propriétés de transport de l'adaptateur TIBCO Enterprise Message Service pour le port de réception
Emplacement de réception pour un système d’exploitation TIBCO Enterprise Message System (EMS) le **URL** et **cible Namespace** au système TIBCO EMS sont les seules valeurs de configuration requises.  
  
### <a name="to-specify-tibco-ems-transport-properties"></a>Pour spécifier les propriétés du transport TIBCO EMS  
  
1.  Développez le **définition système** et entrez les informations requises pour la connexion au serveur TIBCO EMS.  
  
2.  Développez **gestion des messages** et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**Sélecteur de message**|Les messages ne sont reçus que si cette chaîne renvoie True avec le message dans la destination.<br /><br /> Permet au port de réception de ne récupérer que les messages qui contiennent des propriétés d'en-tête correspondant à l'expression décrite dans ce champ.<br /><br /> La syntaxe des sélecteurs de message est basée sur un sous-ensemble de la syntaxe d'expression conditionnelle SQL92. Cette syntaxe est décrite en détail dans le guide de l'utilisateur de TIBCO EMS.<br /><br /> Par exemple, si un message contient un nom de propriété d'en-tête NewsType, un port de réception ne peut récupérer que ceux dont le type est Sports ou Éditorial.|  
    |**Nombre de tentatives**|Nombre de tentatives du transport. Valeur par défaut est 0.|  
    |**Intervalle avant nouvelle tentative**|Délai d'attente avant que l'adaptateur fasse une nouvelle tentative. La valeur par défaut est de cinq minutes.|  
  
3.  Développez le **définition de la connexion serveur** et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**Destination**|Paramètre obligatoire. Définit le nom et le type de la destination. Définit la file d'attente ou la rubrique au format suivant : File d'attente[nom.file.attente] ou Rubrique[nom.rubrique].|  
    |**Numéro de port**|Port sur lequel le serveur TIBCO EMS écoute.|  
    |**Nom de serveur**|Paramètre obligatoire. Nom du système qui héberge le serveur TIBCO EMS.|  
  
4.  Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).  
  
     Vous pouvez utiliser deux méthodes pour accéder au système TIBCO EMS. Vous pouvez utiliser les informations d’identification (paramètres nom et mot de passe d’utilisateur) ou l’authentification unique.  
  
    -   Sélectionnez **Oui** dans **utiliser SSO** à utiliser l’authentification unique.  
  
    -   Sélectionnez une application associée sur la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO EMS. L'adaptateur Microsoft BizTalk pour TIBCO EMS utilise les informations d'identification d'un utilisateur d'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
         Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).  
  
5.  Développez **informations d’identification utilisateur** et entrez le **nom d’utilisateur** et **mot de passe** pour accéder au serveur TIBCO EMS.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Password`|Le mot de passe qui est utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
    |`User Name`|Nom d’un utilisateur qui est utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
  [Création de gestionnaires de réception TIBCO Enterprise Message Service](../core/creating-tibco-enterprise-message-service-receive-handlers.md)