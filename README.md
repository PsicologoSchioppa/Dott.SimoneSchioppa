"use client"

import React, { useState } from "react"
import Image from "next/image"
import { motion, AnimatePresence } from "framer-motion"
import { Card, CardContent } from "@/components/ui/card"
import { Button } from "@/components/ui/button"
import { ChevronDown, Mail, Phone, MapPin, Users, User } from "lucide-react"
import { Playfair_Display } from "next/font/google"

const playfair = Playfair_Display({ subsets: ["latin"] })

export default function Home() {
  const [showServices, setShowServices] = useState(false)
  const [currentImage, setCurrentImage] = useState(0)
  const images = [
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG_3930.jpg-WuUIK343oBMKxz6a8FQtkBzsI3bI4T.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/jpegG_4876-hYzZEcuuDW0AwAAt264DGDH9SIKLLV.jpeg",
  ]

  React.useEffect(() => {
    const timer = setInterval(() => {
      setCurrentImage((prev) => (prev + 1) % images.length)
    }, 5000) // Cambia immagine ogni 5 secondi

    return () => clearInterval(timer)
  }, [])

  const services = [
    "Ansia",
    "Depressione",
    "Attacco di panico",
    "Stress",
    "Disturbi del sonno",
    "Disturbi alimentari",
    "Anoressia",
    "Bulimia",
    "Disturbi psicosomatici",
    "Somatizzazione",
    "Ipocondria",
    "Fobia",
    "Agorafobia",
    "Confusione mentale",
    "Disturbi dell'attenzione",
    "Problemi comportamentali",
    "Disadattamento",
    "Esaurimento nervoso",
    "Insonnia",
    "Dissociazione",
    "Dipendenza affettiva",
    "Disturbi sessuali",
    "Break-down adolescenziale",
    "Crollo psicotico adolescenziale",
    "Alcolismo",
    "Ritardo Cognitivo",
  ]

  // Gestione submit form base
  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault()
    alert("Grazie per aver inviato la richiesta! Ti risponderò presto.")
  }

  return (
    <div className={`min-h-screen font-sans scroll-smooth ${playfair.className}`}>
      {/* Hero Section con immagini dello studio */}
      <section className="relative h-screen flex items-center justify-center overflow-hidden">
        <div className="absolute inset-0 z-0">
          {images.map((img, index) => (
            <motion.div
              key={img}
              className="absolute inset-0"
              initial={{ opacity: 0 }}
              animate={{ opacity: currentImage === index ? 1 : 0 }}
              transition={{ duration: 1 }}
            >
              <div className="relative h-full w-full bg-cover bg-center">
                <Image
                  src={img}
                  alt={`Immagine studio psicologo Simone Schioppa - foto ${index + 1}`}
                  layout="fill"
                  objectFit="cover"
                  priority={index === 0}
                />
                <div className="absolute inset-0 bg-black/40"></div>
              </div>
            </motion.div>
          ))}
        </div>
        <motion.div
          className="relative z-10 text-center p-8 rounded-lg backdrop-blur-sm bg-white/80"
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
        >
          <h1 className="text-6xl font-light tracking-wide mb-4 text-white relative z-10">
            <span className="font-normal">Dr.</span>{" "}
            <span className="font-semibold tracking-wider uppercase text-7xl block mt-2 shadow-text">
              Simone Schioppa
            </span>
          </h1>
          <p className="text-3xl font-semibold text-sky-700 mt-2">Psicologo Clinico</p>
          <p className="mt-6 text-2xl max-w-2xl mx-auto text-gray-700 leading-relaxed">
            Un viaggio di riscoperta di sé attraverso ascolto empatico e consapevolezza.
          </p>
          <motion.div
            className="mt-12"
            animate={{ y: [0, 10, 0] }}
            transition={{ duration: 2, repeat: Number.POSITIVE_INFINITY }}
          >
            <ChevronDown size={40} className="text-white" />
          </motion.div>
        </motion.div>
      </section>

      {/* Chi Sono */}
      <section className="py-20 px-6 md:px-20 bg-gradient-to-br from-white to-sky-50 rounded-t-3xl shadow-lg -mt-10 relative z-10">
        <div className="md:flex items-center gap-12">
          <motion.div
            className="md:w-1/2"
            initial={{ opacity: 0, x: -50 }}
            whileInView={{ opacity: 1, x: 0 }}
            transition={{ duration: 0.8 }}
          >
            <div className="relative h-[400px] w-full rounded-3xl shadow-md hover:shadow-xl transition-shadow duration-300">
              <Image
                src={images[0]}
                alt="Studio del Dr. Simone Schioppa"
                fill
                className="rounded-3xl object-cover"
                priority
              />
            </div>
          </motion.div>
          <motion.div
            className="md:w-1/2 mt-6 md:mt-0"
            initial={{ opacity: 0, x: 50 }}
            whileInView={{ opacity: 1, x: 0 }}
            transition={{ duration: 0.8, delay: 0.2 }}
          >
            <h2 className="text-4xl font-semibold mb-6 text-sky-600">Chi Sono</h2>
            <p className="text-lg leading-relaxed text-gray-700 mb-4">
              Sono uno psicologo clinico, laureato all'Università degli Studi dell'Aquila, dedicato alla promozione del
              benessere psicologico. Il mio approccio si fonda sull'ascolto empatico e sulla creazione di uno spazio
              sicuro per riscoprire se stessi.
            </p>
            <p className="text-lg italic text-sky-600">
              Insieme, esploreremo il tuo mondo interiore per ritrovare equilibrio e serenità.
            </p>
          </motion.div>
        </div>
      </section>

      {/* Servizi */}
      <section className="py-20 px-6 md:px-20 bg-white relative overflow-hidden">
        <h2 className="text-4xl font-semibold mb-12 text-center text-sky-600">Servizi Offerti</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12">
          <motion.div
            className="bg-sky-50 p-6 rounded-xl shadow-md text-center border border-sky-100"
            whileHover={{ scale: 1.05 }}
            whileTap={{ scale: 0.95 }}
          >
            <div className="text-sky-600 mb-4">
              <User size={40} />
            </div>
            <h3 className="text-xl font-semibold text-gray-800">Terapia Individuale</h3>
          </motion.div>
          <motion.div
            className="bg-sky-50 p-6 rounded-xl shadow-md text-center border border-sky-100"
            whileHover={{ scale: 1.05 }}
            whileTap={{ scale: 0.95 }}
          >
            <div className="text-sky-600 mb-4">
              <Users size={40} />
            </div>
            <h3 className="text-xl font-semibold text-gray-800">Terapia di Coppia</h3>
          </motion.div>
        </div>
        <div className="text-center">
          <Button
            onClick={() => setShowServices(!showServices)}
            aria-expanded={showServices}
            aria-controls="extra-services"
            className="bg-sky-600 hover:bg-sky-700 text-white px-8 py-3 rounded-full text-lg transition-all duration-300 shadow-md hover:shadow-lg"
          >
            {showServices ? "Nascondi altri servizi" : "Mostra altri servizi"}
          </Button>
        </div>
        <AnimatePresence>
          {showServices && (
            <motion.div
              id="extra-services"
              className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mt-8"
              initial={{ opacity: 0, height: 0 }}
              animate={{ opacity: 1, height: "auto" }}
              exit={{ opacity: 0, height: 0 }}
              transition={{ duration: 0.5 }}
            >
              {services.map((servizio) => (
                <Card
                  key={servizio}
                  className="bg-sky-50 hover:bg-sky-100 transition-colors duration-300 border border-sky-100"
                >
                  <CardContent className="p-4 text-center font-medium text-gray-700">{servizio}</CardContent>
                </Card>
              ))}
            </motion.div>
          )}
        </AnimatePresence>
      </section>

      {/* Mappa */}
      <section className="py-20 px-6 md:px-20 bg-gradient-to-br from-sky-50 to-white relative overflow-hidden">
        <h2 className="text-4xl font-semibold mb-12 text-center text-sky-600">Dove Trovarmi</h2>
        <div className="bg-white p-8 rounded-3xl shadow-xl">
          <div className="aspect-w-16 aspect-h-9">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3090.470279011074!2d13.397645215018708!3d42.3524091791861!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x13303e4d3e1e14e1%3A0xabc!2sVia%20Cimino%2C%203%2C%2067100%20L'Aquila%20AQ!5e0!3m2!1sit!2sit!4v1612345678901"
              width="100%"
              height="400"
              style={{ border: 0 }}
              allowFullScreen
              loading="lazy"
              referrerPolicy="no-referrer-when-downgrade"
              className="rounded-xl"
              title="Mappa della sede di Dr. Simone Schioppa"
            ></iframe>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-sky-600 text-white py-20 px-6 md:px-20">
        <div className="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12">
          <div>
            <h3 className="text-2xl font-semibold mb-6">Contattami</h3>
            <ul className="space-y-4">
              <li className="flex items-center">
                <MapPin className="mr-2" />
                Via Cimino, 3, 67100 L'Aquila AQ
              </li>
              <li className="flex items-center">
                <Mail className="mr-2" />
                simoneschioppa.psicologo@gmail.com
              </li>
              <li className="flex items-center">
                <Phone className="mr-2" />
                340 141 3347
              </li>
            </ul>
          </div>
          <div>
            <h3 className="text-2xl font-semibold mb-6">Prenota una Consulenza</h3>
            <form className="space-y-4" onSubmit={handleSubmit}>
              <input
                type="text"
                placeholder="Nome"
                required
                aria-label="Nome"
                className="w-full p-3 rounded-md text-gray-800 bg-white/90 backdrop-blur-sm"
              />
              <input
                type="email"
                placeholder="Email"
                required
                aria-label="Email"
                className="w-full p-3 rounded-md text-gray-800 bg-white/90 backdrop-blur-sm"
              />
              <textarea
                placeholder="Messaggio"
                rows={4}
                required
                aria-label="Messaggio"
                className="w-full p-3 rounded-md text-gray-800 bg-white/90 backdrop-blur-sm"
              ></textarea>
              <Button type="submit" className="w-full bg-white text-sky-600 hover:bg-gray-100">
                Invia
              </Button>
            </form>
          </div>
        </div>
        <div className="mt-12 text-center text-sm opacity-75">
          © 2023 Dr. Simone Schioppa. Tutti i diritti riservati.
        </div>
      </footer>
    </div>
  )
}
