import React, { useEffect, useState, useRef } from 'react';
import { motion } from '@/components/motion';
import { Sparkles } from 'lucide-react';

const RoboticsHero = () => {
  const [isTransforming, setIsTransforming] = useState(false);
  const [showDrone, setShowDrone] = useState(false);
  const particlesRef = useRef(null);
  
  // Generate particle positions
  const generateParticles = (count) => {
    return Array.from({ length: count }, (_, i) => ({
      id: i,
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 3 + 1,
      opacity: Math.random() * 0.5 + 0.5
    }));
  };

  const [particles, setParticles] = useState(generateParticles(100));

  useEffect(() => {
    // Start transformation sequence
    const transformationTimer = setTimeout(() => {
      setIsTransforming(true);
      setTimeout(() => {
        setShowDrone(true);
      }, 2000);
    }, 3000);

    return () => clearTimeout(transformationTimer);
  }, []);

  return (
    <div className="relative w-full h-screen bg-gradient-to-br from-gray-900 via-blue-900 to-gray-900 overflow-hidden">
      {/* Holographic Grid */}
      <div className="absolute inset-0 grid grid-cols-12 grid-rows-12 gap-8 opacity-20">
        {Array.from({ length: 144 }).map((_, i) => (
          <div
            key={i}
            className="border border-blue-400/20 rounded-sm"
          />
        ))}
      </div>

      {/* Particle Effect Layer */}
      <div ref={particlesRef} className="absolute inset-0">
        {particles.map((particle) => (
          <motion.div
            key={particle.id}
            className="absolute w-1 h-1 bg-blue-400 rounded-full"
            animate={{
              x: [particle.x + '%', (particle.x + 10) + '%'],
              y: [particle.y + '%', (particle.y + 10) + '%'],
              opacity: [particle.opacity, particle.opacity * 0.5],
            }}
            transition={{
              duration: 3,
              repeat: Infinity,
              repeatType: "reverse",
              ease: "linear"
            }}
            style={{
              left: particle.x + '%',
              top: particle.y + '%',
              width: particle.size,
              height: particle.size,
            }}
          />
        ))}
      </div>

      {/* Robot/Drone Container */}
      <div className="absolute inset-0 flex items-center justify-center">
        <motion.div
          animate={{
            rotateY: isTransforming ? 360 : 0,
            scale: showDrone ? 0.8 : 1,
          }}
          transition={{
            duration: 2,
            ease: "easeInOut"
          }}
          className="relative w-64 h-64"
        >
          {!showDrone ? (
            // Robot SVG
            <svg viewBox="0 0 100 100" className="w-full h-full">
              <motion.path
                d="M20,50 L80,50 M35,30 L65,30 M40,70 L60,70"
                stroke="rgba(59, 130, 246, 0.8)"
                strokeWidth="2"
                fill="none"
                animate={{
                  strokeDasharray: ["0,100", "100,0"],
                }}
                transition={{
                  duration: 2,
                  repeat: Infinity,
                  repeatType: "reverse",
                }}
              />
              <motion.circle
                cx="50"
                cy="50"
                r="25"
                fill="none"
                stroke="rgba(59, 130, 246, 0.8)"
                strokeWidth="2"
                animate={{
                  r: [25, 28],
                  opacity: [1, 0.7],
                }}
                transition={{
                  duration: 1.5,
                  repeat: Infinity,
                  repeatType: "reverse",
                }}
              />
            </svg>
          ) : (
            // Drone SVG
            <motion.svg
              viewBox="0 0 100 100"
              className="w-full h-full"
              animate={{
                y: [0, -10, 0],
                rotate: [0, 5, -5, 0],
              }}
              transition={{
                duration: 4,
                repeat: Infinity,
                repeatType: "reverse",
              }}
            >
              <motion.path
                d="M20,50 L80,50 M50,20 L50,80"
                stroke="rgba(59, 130, 246, 0.8)"
                strokeWidth="2"
                fill="none"
                animate={{
                  strokeDasharray: ["0,100", "100,0"],
                }}
                transition={{
                  duration: 2,
                  repeat: Infinity,
                }}
              />
              <circle cx="50" cy="50" r="15" fill="rgba(59, 130, 246, 0.3)" />
              {[0, 90, 180, 270].map((angle) => (
                <motion.circle
                  key={angle}
                  cx={50 + Math.cos((angle * Math.PI) / 180) * 30}
                  cy={50 + Math.sin((angle * Math.PI) / 180) * 30}
                  r="5"
                  fill="rgba(59, 130, 246, 0.8)"
                  animate={{
                    r: [5, 6],
                    opacity: [1, 0.7],
                  }}
                  transition={{
                    duration: 1,
                    repeat: Infinity,
                    repeatType: "reverse",
                  }}
                />
              ))}
            </motion.svg>
          )}
        </motion.div>
      </div>

      {/* Content Layer */}
      <div className="relative z-10 flex flex-col items-center justify-center h-full text-center">
        <motion.h1
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
          className="text-6xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-teal-400 mb-4"
        >
          YugTroniX Robotics Club
        </motion.h1>
        
        <motion.p
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1, delay: 0.2 }}
          className="text-xl text-blue-200 mb-8"
        >
          Innovating the Future of Robotics
        </motion.p>

        <motion.button
          whileHover={{ scale: 1.05 }}
          whileTap={{ scale: 0.95 }}
          className="px-8 py-3 rounded-full bg-gradient-to-r from-blue-500 to-teal-500 text-white font-semibold relative overflow-hidden group"
        >
          <span className="relative z-10">Join Now</span>
          <motion.div
            className="absolute inset-0 bg-gradient-to-r from-teal-500 to-blue-500"
            animate={{
              opacity: [0, 1],
            }}
            transition={{
              duration: 2,
              repeat: Infinity,
              repeatType: "reverse",
            }}
          />
        </motion.button>
      </div>

      {/* Sparkle Effects */}
      <div className="absolute inset-0 pointer-events-none">
        {Array.from({ length: 20 }).map((_, i) => (
          <motion.div
            key={i}
            className="absolute"
            animate={{
              x: [Math.random() * 100 + '%', Math.random() * 100 + '%'],
              y: [Math.random() * 100 + '%', Math.random() * 100 + '%'],
              opacity: [0, 1, 0],
            }}
            transition={{
              duration: Math.random() * 3 + 2,
              repeat: Infinity,
              repeatType: "loop",
            }}
          >
            <Sparkles className="text-blue-400 w-4 h-4" />
          </motion.div>
        ))}
      </div>
    </div>
  );
};

export default RoboticsHero;
