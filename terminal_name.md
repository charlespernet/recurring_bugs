On a déjà dù vous le demander mais parfois certains élèves ont un nom de terminal qui n'est pas cohérent.

Ex : Certains ont `@Iphone de Julie` sur un Macbook (à la place de `@MacBook-Pro-de-Charles` sur l'image)
![Capture d’écran 2019-07-09 à 11.51.49](https://i.imgur.com/dCJst9T.png)

Ce n'est pas la première promo pour laquelle je vois ça et je viens enfin de comprendre gràce à ce StackOverflow : 

```
  It's perfectly normal for this to occur; when you
  login, Terminal remotely bash does a reverse DNS lookup. 
  It will only be the same if the hostname is not specified
  on the network you're connecting from and there is no reply from
  the DHCP server, or the reverse lookup against the remote DNS server
  fails to resolve.
``` 
https://apple.stackexchange.com/questions/30552/os-x-computer-name-not-matching-what-shows-on-terminal

Cela veut dire que le nom de l'ordinateur n'est pas configuré pour cet utilisateur, et donc le shell va chercher son nom ailleurs.

vous pouvez le vérifier pour confirmer mon intituion en tapant : 
`$ cat /Library/Preferences/SystemConfiguration/preferences.plist`

La clé `ComputerName` est théoriquement manquante.

Pour réparer, il suffit de configurer le nom de l'ordinateur souhaité : 

`Préférences Système > Partagé`

Redémarrer le terminal et le nom devrait être pris.


