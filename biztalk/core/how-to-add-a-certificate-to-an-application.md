---
title: "Comment ajouter un certificat à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, certificates
- managing [certificates], adding to applications
- certificates, applications
- managing [applications], certificates
- managing [certificates], applications
- managing [resources], certificates
ms.assetid: 7c615002-6627-4134-9c2b-bf1c89d626c2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7551e18b1e63f706dfe7e5ff8f951e7aee4f4694
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-certificate-to-an-application"></a>Ajout d'un certificat à une application
Cette rubrique explique comment utiliser une ligne de commande pour ajouter un certificat à une application BizTalk. Cette option n'est pas disponible dans la console Administration de BizTalk Server. Vous ajoutez un certificat à une application BizTalkafin de pouvoir transférer le certificat d'un groupe BizTalk à un autre, au sein d'une application. Les certificats permettent de vérifier les identités et d'établir des liaisons sécurisées pour les ports d'envoi et les emplacements de réception. Pour plus d’informations, consultez [comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md) et [comment attribuer un certificat à un emplacement de réception](../core/how-to-assign-a-certificate-to-a-receive-location.md).  
  
 Lorsque vous ajoutez un certificat à une application, gardez les points importants suivants à l'esprit :  
  
-   Lorsque vous ajoutez un certificat à une application, le certificat est ajouté à la base de données de gestion BizTalk sous forme d'artefact de certificat. Au moment où vous installez l'application, le certificat est importé dans le magasin de certificats Autres personnes sur l'ordinateur local, afin que vous n'ayez pas à exécuter cette étape supplémentaire d'importation dans le magasin pour l'attribuer à un port d'envoi ou à un emplacement de réception. Lorsque vous utilisez BTSTask pour ajouter le certificat, ce dernier doit exister dans le magasin de certificats Autres personnes et vous devez spécifier son empreinte.  
  
    > [!NOTE]
    >  Lorsqu'un certificat est exporté, la clé privée est supprimée. Lorsque l'application est installée, bien que le certificat ait été importée dans le magasin de certificats, il ne peut être utilisé pour déchiffrer un message chiffré, mais il peut par contre être utilisé pour envoyer un message chiffré. Si vous avez besoin du certificat pour la première opération, vous devez le réinstaller dans le magasin de certificats Autres personnes sur l'ordinateur hébergeant le port d'envoi qui utilise le certificat.  
  
-   Si un certificat est utilisé sur un port d'envoi ou un emplacement de réception dans plusieurs applications, il est recommandé de déployer le certificat dans une application distincte, puis de référencer cette application depuis les autres applications qui utilisent le certificat, car il ne peut exister qu'un seul certificat avec une empreinte donnée dans un groupe BizTalk. Par conséquent, il est impossible d'importer le même certificat dans différentes applications. Si vous tentez d'importer deux applications utilisant le même certificat, la première importation réussira, la seconde non. Dans ce cas, l'utilisation de l'option d'importation Remplacer ne résout pas le problème, étant donné que le certificat que vous souhaitez remplacer existe dans une autre application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-add-a-certificate-to-an-application"></a>Pour ajouter un certificat à une application  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **ApplicationName** [**/Overwrite**] **/Overwrite/Thumbprint : «***valeur***»** [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication ApplicationName /Overwrite /overwrite/Thumbprint : "04 a2 8e 32 24 f9 36 b9 42 81 12 71 3 a d2 ef db c7 9c 83 dc « /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk pour laquelle ajouter le certificat. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : Certificate** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un certificat existant. Si cette option n'est pas spécifiée et qu'un certificat, dont l'empreinte est la même que celle du certificat à ajouter, existe déjà dans l'application, l'opération d'ajout échoue. Vous pouvez afficher la propriété Empreinte en double-cliquant sur le certificat dans le composant logiciel enfichable Certificats et en cliquant sur l'onglet Détails. Pour plus d'informations, consultez la rubrique relative à l'affichage des informations sur les certificats dans la documentation du composant logiciel enfichable Certificats.|  
    |**/ Empreinte numérique**|Propriété de l’empreinte numérique du certificat (une *l’empreinte numérique* est un résumé des données). Cette valeur doit être entourée de guillemets doubles (").|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : certificat](../core/addresource-command-certificate.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)