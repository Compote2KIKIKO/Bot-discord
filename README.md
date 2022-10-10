import os
import discord
#import random
import math

from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='@', intents=intents)
my_secret = os.environ['DISCORD_TOKEN']
bot.remove_command('help')




@bot.event
async def on_ready():
  print("Bot connecté en tant que {0.user} !".format(bot))


@bot.command()
async def help(ctx):
    embed = discord.Embed(colour=discord.Colour.blue())
    embed.set_author(name='Liste des commandes pour calculer les Volumes')

    #Commandes User
    embed.add_field(name="**@VCone**", value="Calcule le volume d'un cône. \n *Ecrire @VCone (AireBase) (Hauteur)*   ", inline=False)
    embed.add_field(name="**@VPyramide**", value="Calcule le volume d'une pyramide.   \n *Ecrire @VPyramide (AireBase) (Hauteur)*", inline=False)
    embed.add_field(name="**@VCube**", value="Calcule le volume d'un cube. \n *Ecrire @VCube (Côté)*", inline=False)
    embed.add_field(name="**@VSphere**", value="Calcule le volume d'une sphere. \n *Ecrire @VSphere (Rayon)*   ", inline=False)
    embed.add_field(name="**@VCylindre**", value="Calcule le volume d'un cylindre. \n *Ecrire @VCylindre (AireBase) (Hauteur)*", inline=False)
    embed.add_field(name="**@VPrisme**", value="Calcule le volume d'un prisme. \n *Ecrire @VPrisme (AireBase) (Hauteur)*", inline=False)
    

    await ctx.send(embed=embed)

  

    embed2 = discord.Embed(colour=discord.Colour.red())
    embed2.set_author(name='Liste des commandes pour calculer les Aires')
    

    #Commandes User
    embed2.add_field(name="**@ACarre**", value="Calcule l'aire d'un carré \n *Ecrire @ACarre (Côté)*", inline=False)

    embed2.add_field(name="**@ARectangle**", value="Calcule l'aire d'un rectangle \n *Ecrire @ARectangle (Valeur de l1) (Valeur de l2)* ", inline=False)


    embed2.add_field(name="**@ALosange**", value="Calcule l'aire d'un losange \n *Ecrire @ALosange (Valeur de d1) (Valeur de d2)*", inline=False)


    embed2.add_field(name="**@ADisque**", value="Calcule l'aire d'un disque  \n *Ecrire @ADisque (Rayon)*  ", inline=False)


    embed2.add_field(name="**@ATriangle**", value="Calcule l'aire d'un triangle \n *Ecrire @ATriangle (Longueur) (Hauteur)*  ", inline=False)

    await ctx.send(embed=embed2)

  
    


@bot.command()
async def ACarre(ctx, c: int):

  embed = discord.Embed(colour=discord.Colour.red())
  embed.set_author(name='Aire du carré')
  embed.set_thumbnail(url="https://trucmania.ouest-france.fr/wp-content/uploads/2022/04/aire-carre.jpg")


  embed.add_field(name="**Aire de carré de côté " f"{c}""**", value="L'aire de carré de côté " f"{c} est de {c*c} cm²", inline=False)
  
  await ctx.send(embed=embed)
  




@bot.command()
async def ARectangle(ctx, b: int, h: int):

  embed = discord.Embed(colour=discord.Colour.red())
  embed.set_author(name='Aire du rectangle')
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2011/12/aire-rectangle-exemple.png")


  embed.add_field(name="**Aire de rectangle de longueur " f"{b} et de longueur " f"{h}**", value="L'aire de rectangle de longueur " f"{b} et de longueur " f"{h} est de {b*h} cm²", inline=False)
  
  await ctx.send(embed=embed)
   

  
  



@bot.command()
async def ALosange(ctx, b: int, h: int):

  embed = discord.Embed(colour=discord.Colour.red())
  embed.set_author(name='Aire du losange')
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2013/08/aire-losange.png")


  embed.add_field(name="**Aire de losange de diagoniale " f"{b} et de diagonale " f"{h}**", value="L'aire de losange de diagonale " f"{b} et de diagonale " f"{h} est de {b*h/2} cm²", inline=False)
  
  await ctx.send(embed=embed)

  
  

  



@bot.command()
async def ADisque(ctx, r: int):

  embed = discord.Embed(colour=discord.Colour.red())
  embed.set_author(name='Aire de disque')
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2012/02/aire-disque.png")


  embed.add_field(name="**Aire de disque de rayon " f"{r}""**", value="L'aire de disque de rayon " f"{r} est de {r*r*math.pi} cm²", inline=False)
  
  await ctx.send(embed=embed)
  


  




@bot.command()
async def ATriangle(ctx, b: int, h: int):


  embed = discord.Embed(colour=discord.Colour.red())
  embed.set_author(name='Aire du triangle')
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2012/04/aire-triangle-quelconque-principe.png")


  embed.add_field(name="**Aire de triangle de longueur " f"{b} et de hauteur " f"{h}**", value="L'aire de triangle de longueur " f"{b} et de hauteur " f"{h} est de {b*h/2} cm²", inline=False)
  
  await ctx.send(embed=embed)



  
  await ctx.send("L'aire d'un triangle de longueur " f"{b} et de hauteur " f"{h} est environ égale à  " f"{b*h/2} cm²")

  
  
#Volume

@bot.command()
async def VSphere(ctx, r: int):


  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'une Sphère")
  embed.set_thumbnail(url="https://warmaths.fr/SCIENCES/unites/VOL%20CAPA/spher_fichiers/image009.jpg")


  embed.add_field(name="**Volume d'une Sphère de rayon " f"{r}""**", value="Le volume d'une sphère de rayon " f"{r} est de environ {4/3*math.pi*r*r*r} cm3", inline=False)
  
  await ctx.send(embed=embed)

  

@bot.command()
async def VPyramide(ctx, a: int, h:int):


  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'une Pyramide")
  embed.set_thumbnail(url="https://static1.assistancescolaire.com/4/images/3mso101n01i01.png")


  embed.add_field(name="**Volume d'une Pyramide d'Aire de Base " f"{a} et de Hauteur " f"{h}**", value="Volume d'une Pyramide d'Aire de Base " f"{a} et de Hauteur " f"{h} est de environ {1/3*a*h} cm3", inline=False)
  
  await ctx.send(embed=embed)


@bot.command()
async def VCylindre(ctx, b: int, h: int ):


  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'une Cylindre")
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2012/04/volume-cylindre-exemple.png")


  embed.add_field(name="**Volume d'un Cylindre d'Aire de Base " f"{b} et de Hauteur " f"{h}**", value="Volume d'un cylindre d'Aire de Base " f"{b} et de Hauteur " f"{h} est de environ {b*h} cm3", inline=False)
  
  await ctx.send(embed=embed)





@bot.command()
async def VCone(ctx, b: int, h: int ):

  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'un Cône")
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2015/01/volume-cone.png")


  embed.add_field(name="**Volume d'un Cône d'Aire de Base " f"{b} et de Hauteur " f"{h}**", value="Volume d'une cône d'Aire de Base " f"{b} et de Hauteur " f"{h} est de environ {1/3*b*h} cm3", inline=False)
  
  await ctx.send(embed=embed)



@bot.command()
async def VPrisme(ctx, b: int, h: int ):

  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'un Prisme")
  embed.set_thumbnail(url="https://www.mathsbook.fr/images_exercices/prisme_droit.png")


  embed.add_field(name="**Volume d'un Prisme d'Aire de Base " f"{b} et de Hauteur " f"{h}**", value="Volume d'un prisme d'Aire de Base " f"{b} et de Hauteur " f"{h} est de environ {b*h} cm3", inline=False)
  
  await ctx.send(embed=embed)


  
@bot.command()
async def VCube(ctx, c: int):

  embed = discord.Embed(colour=discord.Colour.blue())
  embed.set_author(name="Volume d'un Cube")
  embed.set_thumbnail(url="https://www.lememento.fr/wp-content/uploads/2012/01/volume-cube.png")


  embed.add_field(name="**Volume d'un Cube de côté " f"{c}""**", value="Le volume d'un cube de côté " f"{c} est de  {c*c*c} cm3", inline=False)
  
  await ctx.send(embed=embed)

  


bot.run(my_secret)
