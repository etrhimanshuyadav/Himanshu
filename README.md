import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Github, Linkedin, Mail, Moon, Sun } from "lucide-react";
import { motion, useScroll, useTransform } from "framer-motion";
import Image from "next/image";
import { useEffect, useState, useRef } from "react";
import Typed from "react-typed";

export default function Portfolio() {
  const [darkMode, setDarkMode] = useState(false);
  const mainRef = useRef(null);
  const { scrollYProgress } = useScroll({ target: mainRef });
  const y = useTransform(scrollYProgress, [0, 1], [0, 300]);
  const rotate = useTransform(scrollYProgress, [0, 1], [0, 15]);

  useEffect(() => {
    document.documentElement.classList.toggle("dark", darkMode);
  }, [darkMode]);

  return (
    <main
      ref={mainRef}
      className="relative min-h-screen bg-gradient-to-tr from-blue-50 via-white to-purple-100 dark:from-gray-900 dark:via-gray-800 dark:to-black p-6 text-gray-800 dark:text-white transition-all overflow-hidden"
    >
      {/* 3D Background Elements with Parallax */}
      <motion.div style={{ y, rotate }} className="absolute inset-0 z-0 pointer-events-none overflow-hidden">
        <div className="absolute w-[30rem] h-[30rem] bg-purple-300 dark:bg-purple-700 rounded-full blur-3xl opacity-30 top-10 left-[-10rem] animate-[float_6s_infinite] will-change-transform"></div>
        <div className="absolute w-80 h-80 bg-blue-300 dark:bg-blue-700 rounded-full blur-2xl opacity-20 bottom-20 right-[-8rem] animate-[spin_20s_linear_infinite] will-change-transform"></div>
        <div className="absolute w-60 h-60 bg-pink-200 dark:bg-pink-600 rounded-full blur-2xl opacity-25 top-[40%] left-[45%] animate-[bounce_5s_infinite] will-change-transform"></div>
      </motion.div>

      {/* Custom keyframes */}
      <style jsx>{`
        @keyframes float {
          0% { transform: translateY(0); }
          50% { transform: translateY(-20px); }
          100% { transform: translateY(0); }
        }
        @keyframes bounce {
          0%, 100% { transform: translateY(0); }
          50% { transform: translateY(-15px); }
        }
      `}</style>

      {/* Dark mode toggle */}
      <div className="relative z-10 flex justify-end mb-4">
        <button
          onClick={() => setDarkMode(!darkMode)}
          className="flex items-center gap-2 px-3 py-1 rounded-md border dark:border-white border-gray-800 text-sm hover:bg-gray-200 dark:hover:bg-gray-700"
        >
          {darkMode ? <Sun className="h-4 w-4" /> : <Moon className="h-4 w-4" />}
          {darkMode ? "Light Mode" : "Dark Mode"}
        </button>
      </div>

      <motion.section
        className="relative z-10 text-center py-10"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6 }}
      >
        <motion.div
          whileHover={{ scale: 1.05, rotate: 2 }}
          className="inline-block"
        >
          <Image
            src="/creative-header.gif"
            alt="Creative Banner"
            width={150}
            height={150}
            className="mx-auto mb-4 rounded-full shadow-md"
          />
        </motion.div>
        <h1 className="text-5xl font-extrabold mb-2 tracking-tight">Himanshu Yadav</h1>
        <Typed
          strings={["🚀 Entrepreneur", "🎨 Creative Developer", "💡 Tech Visionary"]}
          typeSpeed={50}
          backSpeed={30}
          backDelay={1500}
          loop
          className="text-lg text-gray-600 dark:text-gray-300 mb-6 block"
        />
        <motion.div
          className="mt-4 flex justify-center gap-4 flex-wrap"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 0.6 }}
        >
          <Button variant="outline" asChild whileHover={{ scale: 1.1 }}>
            <a
              href="https://github.com/etrhimanshuyadav"
              target="_blank"
              rel="noopener noreferrer"
            >
              <Github className="mr-2 h-4 w-4" /> GitHub
            </a>
          </Button>
          <Button variant="outline" asChild whileHover={{ scale: 1.1 }}>
            <a
              href="https://linkedin.com/in/himanshuyadav2002"
              target="_blank"
              rel="noopener noreferrer"
            >
              <Linkedin className="mr-2 h-4 w-4" /> LinkedIn
            </a>
          </Button>
          <Button variant="outline" asChild whileHover={{ scale: 1.1 }}>
            <a href="mailto:himanshuyadavofficial@gmail.com">
              <Mail className="mr-2 h-4 w-4" /> Email
            </a>
          </Button>
          <Button variant="outline" asChild whileHover={{ scale: 1.1 }}>
            <a
              href="https://instagram.com/etrhimanshuyadav"
              target="_blank"
              rel="noopener noreferrer"
            >
              <Image
                src="/animated-instagram.gif"
                alt="Instagram"
                width={20}
                height={20}
                className="mr-2 rounded-full"
              />
              Instagram
            </a>
          </Button>
        </motion.div>
      </motion.section>
    </main>
  );
}
