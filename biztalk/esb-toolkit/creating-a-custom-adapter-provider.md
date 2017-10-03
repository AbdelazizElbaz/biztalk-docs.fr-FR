---
title: "Création d’un fournisseur de l’adaptateur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb93acf8-fd9d-4315-8690-f0c152a954b5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feb9efa5ad879e86f32ca1963313dadc7e6a9d7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-adapter-provider"></a>Création d’un fournisseur de l’adaptateur personnalisé
Après avoir exécuté un programme de résolution, comme décrit dans les sections précédentes, le service de résolution dynamique vérifie si le résultat est un point de terminaison (et pas une transformation). S’il s’agit d’un point de terminaison, le service instancie le Gestionnaire d’adaptateur, qui est une instance de la **AdapterMgr** classe.  
  
 Le Gestionnaire d’adaptateur valide et résout le type de transport et de l’emplacement de transport sortant. Si le type de transport est toujours pas résolu, et si l’URL commence par « http » ou « https », le Gestionnaire d’adaptateur définit le type de transport à « WCF-WSHttp ».  
  
 Ensuite, le Gestionnaire d’adaptateur vérifie que le type de transport correspond à un adaptateur Microsoft BizTalk Server valid et il retourne son espace de noms de propriété. Ce processus s’exécute qu’une seule fois pour toutes les cartes et stocke les résultats dans un cache afin d’éviter la répétition de requêtes pour les autres messages entrants qui utilisent la même carte.  
  
 Le Gestionnaire d’adaptateur utilise le type de transport (sans le «**://**« suffixe) pour déterminer le fournisseur de l’adaptateur approprié. Un fournisseur de l’adaptateur est un assembly personnalisé doit implémenter la **IAdapterProvider** interface. Le fournisseur de l’adaptateur utilise les propriétés de la **résolution** de la structure dans le **dictionnaire** instance générée par le programme de résolution pour toutes les propriétés spécifiques au protocole du message qui permet de définir le Moteur d’exécution de Microsoft BizTalk Server pour effectuer la résolution dynamique.  
  
 Comme avec le programme de résolution (décrite dans la section précédente), le mécanisme de résolution dynamique utilise les entrées dans le fichier de configuration Esb.config pour localiser des fournisseurs de carte. Le code XML suivant montre la section du fichier de configuration.  
  
```xml  
<adapterProviders cacheManager= "Adapter Providers Cache Manager"  absoluteExpiration="3600">  
     <adapterProvider name="WCF-WSHttp" type="Microsoft.Practices.ESB.Adapter.WcfWSHttp.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfWSHttp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="Http,Https" />  
     <adapterProvider name="WCF-BasicHttp" type="Microsoft.Practices.ESB.Adapter.WcfBasicHttp.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfBasicHttp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="Http,Https" />  
     <adapterProvider name="WCF-Custom" type="Microsoft.Practices.ESB.Adapter.WcfCustom.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfCustom, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="mssql" />  
     <adapterProvider name="SMTP" type="Microsoft.Practices.ESB.Adapter.SMTP.AdapterProvider, Microsoft.Practices.ESB.Adapter.SMTP, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="smtp" />  
     <adapterProvider name="FTP" type="Microsoft.Practices.ESB.Adapter.FTP.AdapterProvider, Microsoft.Practices.ESB.Adapter.FTP, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
          <adapterConfig>  
               <add name="DefaultUsername" value="anonymous" />  
               <add name="DefaultPassword" value="" />  
          </adapterConfig>  
     </adapterProvider>  
     <adapterProvider name="MQSeries" type="Microsoft.Practices.ESB.Adapter.MQSeries.AdapterProvider, Microsoft.Practices.ESB.Adapter.MQSeries, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="MQS" adapterAssembly="MQSeries, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     <adapterProvider name="FILE" type="Microsoft.Practices.ESB.Adapter.FILE.AdapterProvider, Microsoft.Practices.ESB.Adapter.FILE, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="File" />  
</adapterProviders>  
```  
  
## <a name="creating-a-custom-adapter-provider"></a>Création d’un fournisseur de l’adaptateur personnalisé  
 Le Gestionnaire d’adaptateur (une instance de la **AdapterMgr** classe) recherche le fournisseur de l’adaptateur dans les fichiers de configuration et charge l’assembly approprié. Le mécanisme de résolution dynamique met en cache chargé de toutes les implémentations concrètes de la **IAdapterProvider** interface afin d’éviter les répétées de la lecture des informations de configuration et de chargement lors de l’utilisent de plusieurs messages entrants de l’assembly le même fournisseur de l’adaptateur.  
  
 Enfin, le Gestionnaire d’adaptateur s’exécute le **SetEndPoint** méthode de l’implémentation concrète de la **IAdapterProvider** interface et le composant de pipeline renvoie le message à BizTalk Base de données MessageBox.  
  
 **Pour créer un fournisseur de l’adaptateur personnalisé**  
  
1.  Créer un assembly qui dérive de la **BaseAdapterProvider** classe de base et contient un **SetEndPoint** méthode qui définit le point de terminaison des propriétés de contexte du message.  
  
2.  Inscrire le fournisseur de l’adaptateur en l’ajoutant à Esb.config les fichiers de configuration à l’aide un  **\<adapterProvider >** élément avec un nom pour la carte en tant que le **nom** attribut, l’entièrement nom qualifié de la classe en tant que le **type** d’attribut, le moniker comme le **moniker** attribut (plusieurs valeurs doivent être séparés par une virgule) et éventuellement l’assembly de l’adaptateur réel comme le **adapterAssembly** attribut.  
  
3.  Enregistrer le nouvel assembly dans le global assembly cache.