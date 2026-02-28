import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion } from "framer-motion";

export default function ProposalPage() {
  const [noPosition, setNoPosition] = useState({ x: 0, y: 0 });
  const [accepted, setAccepted] = useState(false);

  const moveNoButton = () => {
    const randomX = Math.floor(Math.random() * 200) - 100;
    const randomY = Math.floor(Math.random() * 200) - 100;
    setNoPosition({ x: randomX, y: randomY });
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-pink-100 to-rose-200 flex items-center justify-center p-6 overflow-hidden">
      <motion.div
        initial={{ opacity: 0, y: 40 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.8 }}
        className="max-w-2xl w-full relative"
      >
        <Card className="rounded-2xl shadow-2xl bg-white">
          <CardContent className="p-10 text-center">

            {/* Couple Photo */}
            <motion.img
              src="/couple.jpg"   
              alt="Arjun and Sneha"
              className="w-48 h-48 object-cover mx-auto rounded-full shadow-xl mb-6 border-4 border-pink-200"
              initial={{ scale: 0.8, opacity: 0 }}
              animate={{ scale: 1, opacity: 1 }}
              transition={{ duration: 0.8 }}
            />

            <h1 className="text-4xl font-bold mb-4 text-gray-800">
              Sneha 💖
            </h1>

            {!accepted ? (
              <>
                <p className="text-lg text-gray-600 mb-6">
                  From the moment you came into my life, everything became brighter.
                  Your smile, your laughter, and your love mean everything to me.
                </p>
                <p className="text-lg text-gray-600 mb-10">
                  Sneha, will you make me the happiest man alive and marry me?
                </p>

                <div className="flex justify-center gap-6 relative h-24">
                  <Button
                    onClick={() => setAccepted(true)}
                    className="rounded-2xl px-8 py-4 text-lg"
                  >
                    Yes 💍
                  </Button>

                  <motion.div
                    animate={{ x: noPosition.x, y: noPosition.y }}
                    transition={{ type: "spring", stiffness: 300 }}
                    onMouseEnter={moveNoButton}
                    className="absolute"
                  >
                    <Button
                      variant="outline"
                      className="rounded-2xl px-8 py-4 text-lg"
                    >
                      No 😜
                    </Button>
                  </motion.div>
                </div>
              </>
            ) : (
              <motion.div
                initial={{ scale: 0.5, opacity: 0 }}
                animate={{ scale: 1, opacity: 1 }}
                transition={{ duration: 0.6 }}
                className="mt-6"
              >
                <h2 className="text-3xl font-bold text-pink-600 mb-4">
                  She Said YES!!! 🎉💖
                </h2>
                <p className="text-lg text-gray-600">
                  This is the beginning of our forever. I love you, Sneha ❤️
                </p>
              </motion.div>
            )}

            <div className="mt-10 text-sm text-gray-500">
              Forever yours, <span className="font-semibold">Arjun</span> ❤️
            </div>
          </CardContent>
        </Card>
      </motion.div>
    </div>
  );
}
