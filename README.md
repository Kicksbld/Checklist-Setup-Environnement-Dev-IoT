# 🛠️ Checklist Setup — Environnement Dev IoT

> **Stack :** MacBook Pro 2024 · Mac Mini · Raspberry Pi · ESP32  
> **Réseau central :** `Cudy-FA5C` — mdp : `58448069`

---

## 1. 🖥️ Setup du Mac Mini

- [ ] Brancher l'écran au Mac Mini
- [ ] Brancher le clavier et la souris au Mac Mini
- [ ] Connecter le Mac Mini au Wi-Fi **Cudy-FA5C**
  - Mot de passe : `58448069`
- [ ] Vérifier la connexion internet

---

## 2. 🍓 Démarrage de la Raspberry Pi

- [ ] Brancher la Raspberry Pi en **USB-C** sur le Mac Mini
- [ ] ⏳ Attendre **45 secondes** (démarrage + connexion Wi-Fi)
- [ ] Vérifier que la Raspberry Pi est bien connectée au Wi-Fi **Cudy-FA5C**

---

## 3. 🔌 Branchement de l'ESP32

- [ ] Brancher l'ESP32 en **USB-C** sur le **MacBook Pro**
- [ ] Brancher les composants nécessaires à l'ESP32
- [ ] Ouvrir **Thonny** sur le MacBook Pro
- [ ] Configurer l'ESP32 dans Thonny : `Tools > Options > Interpreter`
  - Sélectionner **MicroPython (ESP32)**
  - Choisir le bon port série

---

## 4. 🍓 Lancement des serveurs sur la Raspberry Pi

Se connecter en SSH depuis le MacBook Pro :

```bash
ssh pi@pi2
```

- [ ] Naviguer dans le dossier du projet :
  ```bash
  cd /python-server-client-main
  ```
- [ ] S'assurer d'être dans le bon **venv** :
  ```bash
  source .venv/bin/activate
  ```
- [ ] Lancer le WebSocket Server :
  ```bash
  python WSServer.py
  ```
- [ ] Dans un **nouveau terminal SSH**, lancer l'app admin :
  ```bash
  ssh pi@pi2
  cd /python-server-client-main
  source .venv/bin/activate
  python admin/app.py
  ```

---

## 5. 💻 Lancement du client WebSocket sur le Mac Mini

Se connecter en SSH depuis le MacBook Pro :

```bash
ssh digital@192.168.10.194
```

- [ ] Naviguer dans le dossier du projet :
  ```bash
  cd python-server-client
  ```
- [ ] Activer le **venv** :
  ```bash
  source .venv/bin/activate
  ```
- [ ] Lancer le WebSocket Client :
  ```bash
  python WSClient.py
  ```

---

## 6. 📟 Lancement de l'ESP32

- [ ] Dans **Thonny**, s'assurer que le script est prêt
- [ ] Appuyer sur le bouton de lancement de l'ESP32
- [ ] ⏳ Attendre la connexion WebSocket de l'ESP32 (message de confirmation dans les logs)

---

## 7. 🖥️ Lancement du Server WebSocket + Interface sur le MacBook Pro

- [ ] Ouvrir un terminal sur le **MacBook Pro**
- [ ] Naviguer dans le dossier du repo Server WebSocket
- [ ] Activer le **venv** :
  ```bash
  source .venv/bin/activate
  ```
- [ ] Lancer l'interface graphique :
  ```bash
  python3 ChatGUI.py
  ```

---

## 8. 🌐 Vérification finale dans le navigateur

- [ ] Ouvrir un navigateur sur le MacBook Pro
- [ ] Aller sur : [http://127.0.0.1:5000/](http://127.0.0.1:5000/)
- [ ] Vérifier que les **3 appareils sont connectés** :
  - [ ] `MAC_KILLIAN`
  - [ ] `ESP_KILLIAN`
  - [ ] `KILLIAN`

---

## 9. ✅ Test de validation

- [ ] Appuyer sur le **bouton branché à l'ESP32**
- [ ] 🔊 Vérifier qu'une **voix sort du Mac** → si oui, tout est opérationnel !

---

## ⚠️ Rappels importants

> **Toujours vérifier que tu es dans le bon `.venv` avant de lancer un script !**

| Dossier | Commande d'activation |
|---|---|
| `/python-server-client-main` (Pi) | `source .venv/bin/activate` |
| `python-server-client` (Mac Mini) | `source .venv/bin/activate` |
| Repo Server WebSocket (MacBook) | `source .venv/bin/activate` |

Un venv actif affiche `(.venv)` au début de ton prompt :
```
(.venv) pi@raspberry:~$
```
