# safira-tech-style
import React from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { FaHeadphones, FaClock, FaChargingStation } from "react-icons/fa";
import { motion } from "framer-motion";

const products = [
  { id: 1, name: "Auriculares Bluetooth", icon: <FaHeadphones />, price: "$120,000" },
  { id: 2, name: "Reloj Inteligente", icon: <FaClock />, price: "$250,000" },
  { id: 3, name: "Cargador Inalámbrico", icon: <FaChargingStation />, price: "$80,000" }
];

export default function SafiraTechStyle() {
  return (
    <div className="bg-black text-white min-h-screen p-6">
      {/* Header */}
      <motion.header 
        className="text-center text-neon-blue text-3xl font-bold mb-6"
        initial={{ opacity: 0, y: -50 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 1 }}
      >
        SAFIRA TECH STYLE
      </motion.header>
      
      {/* Hero Section */}
      <motion.section 
        className="text-center mb-8"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ duration: 1.5 }}
      >
        <h1 className="text-4xl font-bold text-neon-blue">Tecnología con Estilo</h1>
        <p className="text-lg text-gray-400 mt-2">Encuentra los mejores accesorios tech</p>
      </motion.section>
      
      {/* Products */}
      <div className="grid grid-cols-1 sm:grid-cols-3 gap-6">
        {products.map((product) => (
          <motion.div
            key={product.id}
            initial={{ opacity: 0, scale: 0.8 }}
            animate={{ opacity: 1, scale: 1 }}
            transition={{ duration: 0.8 }}
          >
            <Card className="bg-gray-900 text-center p-4 rounded-2xl border-2 border-neon-blue shadow-neon">
              <CardContent>
                <motion.div 
                  className="text-5xl text-neon-blue mb-4"
                  whileHover={{ scale: 1.2 }}
                >
                  {product.icon}
                </motion.div>
                <h2 className="text-xl font-semibold text-neon-blue">{product.name}</h2>
                <p className="text-lg text-gray-400">{product.price}</p>
                <Button className="bg-neon-blue text-black mt-4 hover:bg-neon-glow">Comprar Ahora</Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </div>
    </div>
  );
}
