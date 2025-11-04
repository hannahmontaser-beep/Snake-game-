# Snake-game-
A2 game
#add project details 
def on_on_overlap(sprite2, otherSprite):
    game.game_over(True)
sprites.on_overlap(SpriteKind.player, SpriteKind.enemy, on_on_overlap)

def on_overlap_tile(sprite, location):
    game.game_over(False)
    def on_on_overlap_collectable(sprite3: any, location2: any):
        info.change_score_by(1)

#code for collection chests
def on_overlap_collectable(Sprite, location):
    tiles.set_tile_at(location,assets.image("""transparent"""))
    info.change_score_by(1)
    scene.on_overlap_tile(SpriteKind.player,assets.image("""myimage"""), on_overlap_collectable)


# this is where code starts
info.set_score(1)

# background
scene.set_background_image(assets.image("""
    backdrop
    """))
tiles.set_current_tilemap(tilemap("""chests"""))


# Player controls
my_sprite = sprites.create(assets.image("""
    snakeblock
    """), SpriteKind.player)
controller.move_sprite(my_sprite)
my_sprite.set_scale(1, ScaleAnchor.MIDDLE)
tiles.place_on_tile(my_sprite, tiles.get_tile_location(0, 1))
scene.camera_follow_sprite(my_sprite)


# my enemy code
my_enemy = sprites.create(assets.image("""enemy"""), SpriteKind.player)
my_enemy.set_scale(1, ScaleAnchor.MIDDLE)
tiles.place_on_tile(my_sprite, tiles.get_tile_location(8, 5))
my_enemy.follow(my_sprite)
