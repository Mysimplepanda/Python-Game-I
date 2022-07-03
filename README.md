# 𝓅𝓎𝓉𝒽𝑜𝓃-𝑔𝒶𝓂𝑒-𝒾
### 這是用鍵盤操作的遊戲~使用Pygame module製作。

 ------

**1. _參考資料:_** <br>
  
    1. Pygame Page: http://pygame.org
    2. documentation: http://pygame.org/docs/ref
    3. Icon Archive: https://iconarchive.com/ (下載遊戲角色)
    4. Leshy SFMaker: https://www.leshylabs.com/apps/sfMaker/ (下載音效)
    5. Font Space: https://www.fontspace.com/commercial-fonts (下載字體)
    6. Video Games Music Free Download: https://www.chosic.com/free-music/games/ (下載背景音樂)
    7. 𝔣𝔬𝔫𝔱𝔭𝔞𝔰𝔱𝔢: https://www.fontpaste.com/ (本標題字體是使用這個網站製作)
 ------
 
 **2. _What is pygame? (copied from my first repository)_**
 
    1. Pygame提供Display, Sound, Music, Image, Text, Event幫助製作遊戲。
    2. Pygame可以做出2.0小遊戲
    3. Pygame偵測使用者使用Keyboard, joystick, mouse控制遊戲
    4. Pygame提供許多內建的game objects來製作遊戲
 ------
 
 **3. _introduction of files_**
 
| File | introduction |
|:-----:|:----------:|
| angrybird.png | The main character of this game |
| coin.png | If the anygry_bird touch it, +1 point |
| AttackGraffiti.ttf | The font of this game |
| Feed_The_AngryBird.py | The code :) |
| background_music.wav | background music |
| coin.wav | The sound effect when you touch the coin |
| miss.wav | The sound effect when you don't touch the coin |


 ------
 
 **4. _code snippet_**

```Python
#Blit image object and setting its rec.
player_image        = pygame.image.load("angrybird.png")
player_rect         = player_image.get_rect()
player_rect.left    = 32
player_rect.centery = WINDOW_HEIGHT//2

### while running~
displayscreen.blit(player_image, player_rect)
```

```Python
#check_for_gameover
if lives == 0:
  displayscreen.blit(gameover_text, gameover_text_rect)
  displayscreen.blit(continue_text, continue_text_rect)
  pygame.display.update()
  pygame.mixer.music.stop()
        
  is_paused = True
  while is_paused:
    for event in pygame.event.get():
      if event.type == pygame.QUIT:
        is_paused = False
        running   = False
                    
      if event.type == pygame.KEYDOWN:
        score         = 0
        lives         = PLAYER_STARTING_LIVES
        player_rect.y = WINDOW_HEIGHT//2
        coin_velocity = COIN_STARTING_VELOCITY
        pygame.mixer.music.play(-1, 0.0)
        is_paused    = False
```
```Python
#create the displayscreen
WINDOW_WIDTH,WINDOW_HEIGHT = 1000, 600
displayscreen = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
pygame.display.set_caption("Feed The Angry Bird! ")

```
```Python
#Check the collision
if player_rect.colliderect(coin_rect):
  score+=1
  coin_sound.play()
  coin_velocity += COIN_ACCELERATION
  coin_rect.x = WINDOW_WIDTH + BUFFER_DISTANCE
  coin_rect.y = random.randint(64, WINDOW_HEIGHT-32)
```
```Python
#Key move
keys = pygame.key.get_pressed()
if keys[pygame.K_UP] and player_rect.top > 64:
  player_rect.y -= PLAYER_VELOCITY

if keys[pygame.K_DOWN] and player_rect.bottom < WINDOW_HEIGHT:
  player_rect.y += PLAYER_VELOCITY
```


 -----
 
**_5. Game Assets:_**
  
  * [Icon Arxhive: ](https://iconarchive.com/) 網站提供很多遊戲角色下載
  * [Leshy SFMaker: ](https://www.leshylabs.com/apps/sfMaker/) 網站可以下載遊戲特效, 也可以簡單自己製作音效
  * [Video Games Music Free Download: ](https://www.chosic.com/free-music/games/) 可以下再不會被告的遊戲背景音樂
  
<img src="https://raw.githubusercontent.com/Mysimplepanda/Python-Game-I/main/fts_p.png" width="400" height="300" alt="2.py程式截圖"><br> 
