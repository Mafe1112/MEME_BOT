import discord
from discord.ext import commands
import os, random

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix = "$", intents = intents)

@bot.event
async def on_ready():
    print(f"Bot conectado como {bot.user}")

@bot.command()
async def meme(ctx):
    img_name = random.choice(os.listdir("images"))
    with open(f"images/{img_name}", "rb") as f:
        picture = discord.File(f)

    await ctx.send(file=picture)

bot.run("MTM5MjY1MTI2MjA3OTc5NTIzMQ.GoADsz.hslwU4d2DoDxjkS_q6r_dcVMeq0lW_zorQfUYY")
