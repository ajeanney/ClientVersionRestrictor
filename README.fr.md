# ClientVersionRestrictor

N'acceptez que les versions de Minecraft que vous supportez : le plugin lit la version de protocole avec laquelle chaque joueur se connecte, via ViaVersion, et expulse ceux qui sont en dehors de la plage que vous avez configurée.

## Fonctionnalités

- Une version de protocole minimale et une maximale dans la configuration ; laissez le maximum à `-1` pour ne fixer qu'un minimum.
- Fonctionne avec toutes les versions clientes que ViaVersion accepte, le contrôle utilisant le numéro de protocole plutôt que le nom de la version.
- `clientversionrestrictor.bypass` permet à un joueur, ou à tout un groupe, de passer outre le contrôle.
- Le message d'expulsion est configurable, et le joueur est expulsé quelques secondes après sa connexion plutôt que sur l'écran de connexion, il a donc le temps de le lire.

## Prérequis

- Spigot 1.16 ou supérieur (compilé contre l'API 1.20.2).
- [ViaVersion](https://viaversion.com/), déclaré comme dépendance obligatoire : c'est lui qui indique au plugin quelle version utilise un client.

## Installation

1. Déposez le jar compilé dans le dossier `plugins/` de votre serveur, à côté de ViaVersion.
2. Démarrez le serveur une fois pour générer `plugins/ClientVersionRestrictor/config.yml`.
3. Réglez `minVersion` et `maxVersion` sur les numéros de protocole que vous voulez accepter.

## Configuration

```yaml
kickMessage: "§cYou are using an unsupported version of Minecraft!"
minVersion: 472
maxVersion: -1
```

- `minVersion` : le numéro de protocole le plus bas accepté.
- `maxVersion` : le plus haut accepté, ou `-1` pour aucune limite haute.
- `kickMessage` : ce qui est affiché au joueur expulsé, codes couleur compris.

Les numéros de protocole sont ceux utilisés par Minecraft sur le réseau : 754 correspond à la 1.16.5, 763 à la 1.20.1 et 767 à la 1.21. La liste complète se trouve sur le [wiki Minecraft](https://minecraft.wiki/w/Protocol_version).

## Permissions

| Permission | Description |
| --- | --- |
| `clientversionrestrictor.bypass` | Autorise le joueur à se connecter avec n'importe quelle version |

## Compilation

```sh
./gradlew build
```

Le jar est écrit dans `build/libs/`.
