---
title: Installer et configurer la gestion des API REST | Documents Microsoft
description: "Interroger les artefacts dans votre environnement BizTalk à l’aide des données de gestion des API REST avec Feature Pack dans BizTalk Server"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c207b0aca5f2673e615167f75f7f1c7c3fb0e042
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a>Installer et configurer l’API REST de gestion dans BizTalk Server

## <a name="what-are-management-data-apis"></a>Quelles sont les données de gestion des API
API de données de gestion est des points de terminaison qui vous permettent de mettre à jour à distance, ajouter et interroger l’état des différents artefacts dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement. Les points de terminaison sont ajoutés à l’aide de REST et être accompagnée d’une définition swagger. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , il existe un script Windows PowerShell qui installe ces API REST et leurs définitions swagger. Ces API effectuer des appels REST pour gérer à distance des ports, orchestrations, partenaires, accords, pipelines et bien plus encore. 

## <a name="prerequisites"></a>Conditions préalables
* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé. Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md). Vérifier IIS est installé sur le serveur BizTalk en ouvrant **Gestionnaire des Services Internet**. 

## <a name="step-1-install-the-rest-apis"></a>Étape 1 : Installer l’API REST

1. Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**). 
2. Accédez au dossier d’installation de BizTalk (par exemple, tapez : `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).
3. Dans le texte suivant, remplacez `Default Web Site`, `mgmtServiceAppPool`, `domain/user`, `password`, et `domain\group` avec vos valeurs :

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    Dans l’exemple suivant, nous utilisons le `Default Web Site`, créer un pool d’applications nommé `RESTAppPool`, exécuter le pool d’applications en tant que le `bootcampbts2016\btsservice` de compte, utilisez `BIZTALK-serviceacct` comme mot de passe utilisateur, puis donnez aux autorisations du groupe les administrateurs BizTalk Server. Veillez à entrer le texte suivant, y compris le seul devis environnantes valeurs avec des espaces : 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    Lorsque vous avez terminé, le **BizTalkManagementService** application est créée dans IIS :  
    ![Application de BizTalkManagementService](../core/media/biztalkmanagementservice-apppool.png)

4. Pour vérifier qu’il fonctionne, accédez à `http://localhost/BizTalkManagementService/swagger`. Si vous êtes invité à la connexion, connectez-vous avec un compte qui est membre de la domaine\groupe que vous avez entré à l’étape précédente (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`). 

> [!WARNING]
> L’application BizTalkManagementService dans IIS utilise un fichier web.config. Éléments dans le fichier web.config **respectent la casse**. Par conséquent, lorsque vous exécutez le script Windows PowerShell, veillez à entrer la casse correcte pour `-AuthorizationRoles` valeur. Si vous ne savez pas le cas, Voici un moyen simple de déterminer : 
> 
> 1. Ouvrez **gestion de l’ordinateur**, développez **utilisateurs et groupes locaux**.
> 2. Sélectionnez **groupes**et faites défiler jusqu'à la **SQLServer...** groupes. 
> 3. Dans l’exemple suivant, notez **BOOTCAMPBTS2016** est en majuscules. Si vous voyez tout en majuscules, puis entrez le nom d’ordinateur dans tout en majuscules. 
> 
> ![Nom de l’ordinateur est en majuscules](../core/media/groups-case.png)

Maintenant que les API REST sont exposées via IIS, ils peuvent accessibles et exécutées par les autres applications. 

Vous pouvez modifier qui a accès à la mise à jour manuellement la **web.config** fichier, qui se trouve dans le dossier racine de l’application de gestion. Par exemple, utilisez le code suivant à autoriser tout le monde l’accès à la swagger de sortie : 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a>Étape 2 : Tester les API

1. Sur le serveur BizTalk Server, accédez à `http://localhost/BizTalkManagementService/swagger`.

2. Faites défiler vers **hôtes**, puis sélectionnez **afficher/masquer**. Il existe une commande GET ; Cliquez sur cette ligne :  
![OBTENIR tous les ordinateurs hôtes](../core/media/managment-rest-apis-hosts-get.png)

3. Il affiche les détails. Sélectionnez **essayez-le**:  
![À votre tour d’essayer](../core/media/managment-rest-apis-hosts-tryitout.png)

4. Le corps de réponse retourne tous les hôtes :  
![Réponses](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> Si vous y accédez `http://localhost/BizTalkManagementService`, vous devez obtenir une erreur 500. C’est une bonne chose. Il suffit d’ajouter `/swagger` à la fin de l’URL et vous verrez les API REST disponible. 


## <a name="see-also"></a>Voir aussi
 [Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)