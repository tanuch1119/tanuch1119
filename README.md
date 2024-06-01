import discord
from discord.ext import commands

import discord_buttons_plugin
import requests

bot = commands.Bot(command_prefix="?", intents=discord.Intents.all())

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
    except KeyError:
        pass

bot.run("0000000000000")
