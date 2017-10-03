---
title: "Comment ajouter un répertoire virtuel à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directories
- managing [applications], virtual directories
- applications, virtual directories
- virtual directories, applications
ms.assetid: a5726696-bd65-49d9-8814-a078afe8c067
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26627387a65b19cef8146cee8b91b2a7a0919059
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-virtual-directory-to-an-application"></a>Ajout d'un répertoire virtuel à une application
Cette rubrique explique comment ajouter un répertoire virtuel à une application BizTalk à l'aide de l'outil de ligne de commande BTSTask. Cette option n'est pas disponible dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez ajouter un répertoire virtuel si vous avez écrit un service Web personnalisé ou créé un site Web ASP.NET pour disposer d'une interface avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et que vous souhaitiez déployer le répertoire virtuel avec l'application.  
  
 Une autre méthode pour ajouter un répertoire virtuel pour une application est en spécifiant un répertoire virtuel pour un SOAP ou HTTP un emplacement de réception, comme décrit dans [comment configurer un emplacement de réception HTTP](../core/how-to-configure-an-http-receive-location.md). Quelle que soit la méthode choisie, le répertoire virtuel est ajouté à la base de données de gestion BizTalk. Lorsque vous ajoutez un répertoire virtuel à l’aide de la ligne de commande, il affiche également dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans le dossier ressources de l’application à laquelle vous l’avez ajouté, ainsi que la liste des artefacts de l’application lorsque vous utilisez la [Commande ListApp](../core/listapp-command.md). Si vous exportez par la suite l'application, puis l'importez dans une autre groupe BizTalk, le répertoire virtuel s'affiche dans le dossier Ressources.  
  
 Lors de l'ajout d'un répertoire virtuel à une application, gardez les points suivants à l'esprit :  
  
-   Vous pouvez remplacer un répertoire virtuel qui existe déjà dans l'application en spécifiant l'option de remplacement. L’option de remplacement est requise uniquement lorsque le répertoire virtuel existant porte le même nom que celui que vous souhaitez ajouter. Si non spécifié et qu’un répertoire virtuel existe déjà dans l’application avec le même nom que celui en cours d’ajout, l’opération d’ajout échoue.  
  
-   Lorsque vous ajoutez un répertoire virtuel dont l'URL contient « https », préférez l'utilisation de « http » à celle de « https » dans l'URL que vous spécifiez. Si vous utilisez « https », l'opération consistant à ajouter un répertoire virtuel échoue. Bien que vous ajoutiez le répertoire en utilisant « http » dans l'URL, le paramètre « https » correspondant à l'URL dans la métabase des services Internet est activé, de sorte que le répertoire virtuel fonctionne correctement.  
  
-   Si vous ajoutez un répertoire virtuel depuis une version 64 bits du service Web et essayez d'installer l'application comprenant ce répertoire sur un ordinateur 32 bits, le répertoire virtuel ne sera pas installé. Il doit être installé sur un ordinateur 64 bits.  
  
> [!IMPORTANT]
>  Lorsque vous importez une application contenant un répertoire virtuel, les paramètres de sécurité du répertoire virtuel utilisés sont ceux qui sont activés lorsque le fichier .msi est généré au cours de l'exportation de l'application. Si vous déployez une application dans un environnement de production, vérifiez que les paramètres répondent à vos exigences en matière de sécurité avant de l'exporter.  
>   
>  Toutefois, si le répertoire virtuel existe déjà dans l'environnement de destination, les paramètres de sécurité du répertoire virtuel existant seront utilisés. Ils ne sont pas modifiés afin de correspondre à ceux du répertoire virtuel que vous déployez. Dans ce cas, vous devez vérifier qu'ils répondent à vos exigences.  
  
> [!CAUTION]
>  Si le répertoire virtuel utilise le protocole HTTPS (Hypertext Transfer Protocol over Secure Socket Layer), ses paramètres de sécurité ne sont pas conservés lors de l'exportation, et lorsqu'il est importé, il hérite de ceux du répertoire racine. Vous devez vérifier que ces paramètres de sécurité répondent à vos exigences.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-add-a-virtual-directory-to-an-application"></a>Pour ajouter un répertoire virtuel à une application  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [/**ApplicationName :***valeur*] **/Type:System.BizTalk:WebDirectory**[**/Overwrite**] **/Source :***valeur* [**facultatif /Destination :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddResource, /ApplicationName:MyApplication/type : System.BizTalk : WebDirectory /overwrite /Source:http://Host1:90 / MyVirtualDirectory /Destination:http://Host2:90 / / Database de MyVirtualDirectory /Server:MyDatabaseServer : BizTalkMgmtDb**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter le répertoire virtuel. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : WebDirectory** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un répertoire virtuel existant. Si cette option n'est pas spécifiée et qu'un répertoire virtuel, dont le nom est le même que celui du répertoire virtuel à ajouter, existe déjà dans l'application, l'opération AddResources échoue.|  
    |**/ Source**|URI du répertoire virtuel source.|  
    |**Et de destination**|URI à affecter au répertoire virtuel lorsque l'application est installée à partir du fichier .msi. Si ce paramètre n'est pas spécifié, la valeur utilisée est celle du paramètre Source, où l'hôte est défini sur « localhost ».|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : Répertoire virtuel](../core/addresource-command-virtual-directory.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)