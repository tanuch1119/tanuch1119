import discord
from discord.ext import commands

import discord_buttons_plugin
import requests

bot = commands.Bot(command_prefix="?", intents=discord.Intents.all())

@bot.command()
async def ping(ctx):
    raw_ping = bot.latency
    ping = round(raw_ping * 1000)
    await ctx.reply(f"BotのPing値は{ping}msです。")

@bot.event
async def on_ready():
    print("botが正常に起動しました！")
    await bot.change_presence(activity=discord.Game(name="VER:2.4"))

#?bw
@bot.command()
async def bw(ctx):
    await ctx.send(
        "@here みんなーBEDWARSの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?bedwars
@bot.command()
async def bedwars(ctx):
    await ctx.send(
        "@here みんなーBEDWARSの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?mineman
@bot.command()
async def mineman(ctx):
    await ctx.send(
        "@here みんなーMINEMANの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?duel
@bot.command()
async def duel(ctx):
    await ctx.send(
        "@here みんなーDUELの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?Hypixel
@bot.command()
async def Hypixel(ctx):
    await ctx.send(
        "@here みんなーBEDWARSの募集がかけられてるよーーみんなVCに集まれーー"
    )
    
#?hp
@bot.command()
async def hp(ctx):
    await ctx.send(
        "@here みんなーBEDWARSの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?valo
@bot.command()
async def valorant(ctx):
    await ctx.send(
        "@here みんなーVALORANTの募集がかけられてるよーーみんなVCに集まれーー"
    )

#?list
@bot.command()
async def list(ctx):
    view = discord.ui.View()
    view.add_item(
        discord.ui.Button(
            label="ver 1.0",
            style=discord.ButtonStyle.green,
            custom_id="ver1.0"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="ver 1.1",
            style=discord.ButtonStyle.green,
            custom_id="ver1.1"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="ver 2.0",
            style=discord.ButtonStyle.green,
            custom_id="ver2.0"
        )
    )
    await ctx.send("version選んで!", view=view)

@bot.event
async def on_interaction(interaction: discord.Interaction):
    try:
        if interaction.data["component_type"] == 2:
            if interaction.data["custom_id"] == "ver1.0":
                await interaction.response.send_message("Ver.1.0 Changelog: "
                    "基本的な機能追加", ephemeral=True)
            if interaction.data["custom_id"] == "ver1.1":
                await interaction.response.send_message(
                    "Ver.1.1 Changelog: ./help !valo などを追加しました", ephemeral=True
                )
            if interaction.data["custom_id"] == "ver2.0":
                await interaction.response.send_message(
                    "Ver2.0 Changelog: コードを変更しました", 
                    ephemeral=True
                )
            if interaction.data["custom_id"] == "たぬ鯖":
                await interaction.response.send_message(
                    "**tms.vgg.jp**", 
                    ephemeral=True
                )
            if interaction.data["custom_id"] == "みい鯖":
                await interaction.response.send_message(
                    "**mii0516.aternos.me**", 
                    ephemeral=True
                )
            if interaction.data["custom_id"] == "yone鯖":
                await interaction.response.send_message(
                    "**yoneserver.f5.si**", 
                    ephemeral=True
                )
    except KeyError:
        pass

#?server
@bot.command()
async def server(ctx):
    view = discord.ui.View()
    view.add_item(
        discord.ui.Button(
            label="タヌ鯖",
            style=discord.ButtonStyle.blurple,
            custom_id="たぬ鯖"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="みい鯖",
            style=discord.ButtonStyle.blurple,
            custom_id="みい鯖"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="yone鯖",
            style=discord.ButtonStyle.primary,
            custom_id="yone鯖"
        )
    )
    await ctx.send("知りたいipのクリックしてね!", view=view)

#?s
@bot.command()
async def s(ctx):
    view = discord.ui.View()
    view.add_item(
        discord.ui.Button(
            label="タヌ鯖",
            style=discord.ButtonStyle.blurple,
            custom_id="たぬ鯖"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="みい鯖",
            style=discord.ButtonStyle.blurple,
            custom_id="みい鯖"
        )
    )
    view.add_item(
        discord.ui.Button(
            label="yone鯖",
            style=discord.ButtonStyle.primary,
            custom_id="yone鯖"
        )
    )
    await ctx.send("知りたいipのクリックしてね!", view=view)

bot.run("0000000000000000000")
