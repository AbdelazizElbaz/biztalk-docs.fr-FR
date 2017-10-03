---
title: "Interface IStaticAdapterConfig de l’adaptateur statique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f5de01-0cfc-456a-a52b-28f8f076bdfc
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8d95ba4a5945cb43e3681055750cdad628759
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="static-adapter-istaticadapterconfig-interface"></a>Interface IStaticAdapterConfig de l'adaptateur statique
Un adaptateur de conception statique doit implémenter la **IStaticAdapterConfig** interface. Celle-ci lui permet de communiquer avec l'Assistant Ajouter les métadonnées de l'adaptateur et d'obtenir des organisations de service et des descriptions de service individuel à partir de l'adaptateur. L’Assistant appelle les **GetServiceOrganization** et **GetServiceDescription** de projet dans les méthodes pour extraire des informations de métadonnées avec lequel l’adaptateur interagit et l’ajouter à un BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 Le **GetServiceOrganization** méthode obtient une instance de document XML qui représente l’organisation hiérarchique des services exposés de l’adaptateur. Cette structure génère l’arborescence d’organisation de service que vous voyez sur le **sélectionner les Services à importer** page de l’Assistant Ajout de métadonnées d’adaptateur.  
  
 Après avoir sélectionné les services à importer, l’Assistant appelle les **GetServiceDescription** pour obtenir un tableau de fichiers Web Services Description Language (WSDL) correspondant aux catégories de service qui ont été sélectionnés dans la zone Ajouter (méthode) Arborescence de l’Assistant de métadonnées adaptateur. Les schémas représentant les services sont créés en tant que fichiers XSD et sont ajoutés à votre projet BizTalk une fois que vous avez terminé l'Assistant Ajouter les métadonnées de l'adaptateur.  
  
 Dans l’exemple d’adaptateur de fichier, le **GetServiceOrganization** et **GetServiceDescription** méthodes se trouvent dans le **StaticAdapterManagement** classe dans le Fichier de classe AdapterManagement.cs. L’Assistant appelle les **GetServiceOrganization** méthode pour obtenir la structure arborescente à afficher sur le **sélectionner les Services à importer** page. Dans **GetServicesOrganization** le codé en dur retourne la valeur du fichier AdapterManagement.CategorySchema.xml est utilisée comme indiqué dans le fragment de code suivant. En tant que développeur d'adaptateur, vous devrez ajouter la logique pour renvoyer le fichier XML approprié.  
  
```  
public string GetServiceOrganization(IPropertyBag endPointConfiguration, string NodeIdentifier)   
{  
   string result = GetResource("AdapterManagement.CategorySchema.xml");  
   return result;  
}  
```  
  
> [!NOTE]
>  Assurez-vous de modifier le **GetServiceDescription** méthode de la **StaticAdapterManagement** (classe) et non de la **DynamicAdapterManagement** (classe), qui apparaît en premier dans le fichier.  
  
 Le code suivant est issu le **GetServiceDescription** méthode du fichier AdapterManagement.cs. Le fichier service1.wsdl est codé en dur en tant que fichier WSDL renvoyé. Il renvoie des schémas représentés en tant que fichiers WSDL. Le `wsdls` paramètre est un tableau de références WSDL uniques qui correspondent aux références WSDL dans le XML source chargé par **GetServicesOrganization**. Le jeu de descriptions WSDL retourné est utilisé pour générer les types de port et les types de messages pour le projet BizTalk. Si plusieurs types de schéma sont sélectionnables dans l'arborescence, plusieurs fichiers WSDL sont nécessaires. Si vous avez le choix entre plusieurs schémas et plusieurs fichiers WSDL, vous pouvez ajouter une consultation de base de données pour garantir le renvoi du fichier WSDL correct.  
  
```  
/// <summary>     
        /// Get the WSDL file name for the selected WSDL  
        /// </summary>  
        /// <param name="wsdls">place holder</param>  
        /// <returns>An empty string[]</returns>  
        public string[] GetServiceDescription(string[] wsdls)   
      {  
            string[] result = new string[1];  
            result[0] = GetResource("AdapterManagement.service1.wsdl");  
            return result;  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur de conception statique](../core/static-design-time-adapter-configuration.md)