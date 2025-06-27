# GardenImperial
"use client"

import { Button } from "@/components/ui/button"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card"
import { Badge } from "@/components/ui/badge"
import { Separator } from "@/components/ui/separator"

interface Pet {
  name: string
  price: string
  emoji: string
  rarity: string
  abilities: string[]
  description: string
  catchyText: string
}

const pets: Pet[] = [
  {
    name: "Raccoon",
    price: "R$ 15,00",
    emoji: "🦝",
    rarity: "Comum",
    abilities: ["Coleta Noturna", "Resistência +20%", "Velocidade de Plantio +15%"],
    description: "O companheiro perfeito para aventuras noturnas no jardim!",
    catchyText: "🌙 DOMINE A NOITE! Este esperto raccoon trabalha enquanto você dorme!",
  },
  {
    name: "Disco Bee",
    price: "R$ 45,00",
    emoji: "🕺🐝",
    rarity: "Épico",
    abilities: ["Dança da Polinização", "Boost de Flores +50%", "Multiplicador de Mel x3"],
    description: "A abelha mais estilosa do jardim que faz suas flores dançarem!",
    catchyText: "✨ DANCE PARA O SUCESSO! Transforme seu jardim numa pista de dança!",
  },
  {
    name: "Queen Bee",
    price: "R$ 120,00",
    emoji: "👑🐝",
    rarity: "Lendário",
    abilities: ["Comando Real", "Produção de Mel x10", "Invoca Abelhas Trabalhadoras", "Boost Supremo +100%"],
    description: "A majestade das abelhas que governa todo o jardim com elegância!",
    catchyText: "👑 REINE SUPREMA! A rainha que transforma qualquer jardim em império!",
  },
  {
    name: "Red Fox",
    price: "R$ 35,00",
    emoji: "🦊",
    rarity: "Raro",
    abilities: ["Caça ao Tesouro", "Faro Especial", "Velocidade Extrema +40%", "Sorte +25%"],
    description: "Astuta e veloz, esta raposa encontra os melhores tesouros escondidos!",
    catchyText: "🔥 ASTÚCIA PURA! Descubra segredos que outros jamais encontrarão!",
  },
  {
    name: "Dragonfly",
    price: "R$ 25,00",
    emoji: "🪲",
    rarity: "Incomum",
    abilities: ["Voo Ágil", "Controle de Pragas", "Boost de Água +30%", "Visão Panorâmica"],
    description: "Elegante e eficiente, protege seu jardim voando graciosamente!",
    catchyText: "💎 ELEGÂNCIA EM MOVIMENTO! Proteja seu jardim com estilo incomparável!",
  },
]

const rarityColors = {
  Comum: "bg-gray-500",
  Incomum: "bg-green-500",
  Raro: "bg-blue-500",
  Épico: "bg-purple-500",
  Lendário: "bg-yellow-500",
}

interface SalesPageProps {
  username: string
}

export default function SalesPage({ username }: SalesPageProps) {
  return (
    <div className="min-h-screen bg-gradient-to-br from-black via-gray-900 to-cyan-900">
      {/* Header */}
      <div className="bg-black/50 border-b border-cyan-500 p-4">
        <div className="max-w-6xl mx-auto flex justify-between items-center">
          <div>
            <h1 className="text-2xl font-bold text-cyan-400">Grow a Garden - Loja Exclusiva</h1>
            <p className="text-cyan-200">Bem-vindo, {username}!</p>
          </div>
          <div className="text-cyan-300">
            <span className="text-sm">🎮 Roblox Player</span>
          </div>
        </div>
      </div>

      {/* Main Content */}
      <div className="max-w-6xl mx-auto p-6">
        <div className="text-center mb-8">
          <h2 className="text-4xl font-bold text-cyan-400 mb-4">🌟 PETS EXCLUSIVOS 🌟</h2>
          <p className="text-xl text-cyan-200">Transforme seu jardim com estes companheiros únicos!</p>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {pets.map((pet, index) => (
            <Card
              key={index}
              className="bg-black/80 border-cyan-500 border-2 hover:border-cyan-400 transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-cyan-500/20"
            >
              <CardHeader className="text-center">
                <div className="text-6xl mb-2">{pet.emoji}</div>
                <CardTitle className="text-2xl text-cyan-400">{pet.name}</CardTitle>
                <div className="flex justify-center gap-2 items-center">
                  <Badge className={`${rarityColors[pet.rarity as keyof typeof rarityColors]} text-white`}>
                    {pet.rarity}
                  </Badge>
                  <span className="text-2xl font-bold text-green-400">{pet.price}</span>
                </div>
                <CardDescription className="text-cyan-200 font-medium">{pet.description}</CardDescription>
              </CardHeader>

              <CardContent className="space-y-4">
                <div className="bg-cyan-900/30 p-3 rounded-lg border border-cyan-700">
                  <p className="text-cyan-300 font-bold text-center text-sm">{pet.catchyText}</p>
                </div>

                <Separator className="bg-cyan-700" />

                <div>
                  <h4 className="text-cyan-400 font-bold mb-2">🚀 Habilidades Especiais:</h4>
                  <ul className="space-y-1">
                    {pet.abilities.map((ability, abilityIndex) => (
                      <li key={abilityIndex} className="text-cyan-200 text-sm flex items-center">
                        <span className="text-cyan-400 mr-2">•</span>
                        {ability}
                      </li>
                    ))}
                  </ul>
                </div>

                <Button className="w-full bg-gradient-to-r from-cyan-500 to-cyan-600 hover:from-cyan-600 hover:to-cyan-700 text-black font-bold py-3 text-lg transition-all duration-300">
                  💎 COMPRAR AGORA
                </Button>
              </CardContent>
            </Card>
          ))}
        </div>

        {/* Footer */}
        <div className="mt-12 text-center bg-black/50 p-6 rounded-lg border border-cyan-500">
          <h3 className="text-2xl font-bold text-cyan-400 mb-2">🎁 OFERTA ESPECIAL PARA {username.toUpperCase()}!</h3>
          <p className="text-cyan-200 mb-4">Compre 2 pets e ganhe 20% de desconto no terceiro!</p>
          <Button className="bg-gradient-to-r from-yellow-500 to-orange-500 hover:from-yellow-600 hover:to-orange-600 text-black font-bold px-8 py-3 text-lg">
            🔥 APROVEITAR OFERTA
          </Button>
        </div>
      </div>
    </div>
  )
}

   



