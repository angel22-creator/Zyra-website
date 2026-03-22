# Zyra-study-store
import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import {
  Search, Menu, X, Instagram, Facebook, Twitter, Youtube,
  BookOpen, Palette, Ruler, Backpack,
  Mail, Phone, MapPin, Send, Heart,
} from "lucide-react";
import { useToast } from "@/hooks/use-toast";
import heroBg from "@/assets/hero-bg.jpg";

const categories = [
  { icon: BookOpen, title: "Notebooks & Journals", description: "Aesthetic covers, dotted, lined & blank pages for every need." },
  { icon: Palette, title: "Pens & Highlighters", description: "Vibrant colors and smooth ink for beautiful note-taking." },
  { icon: Ruler, title: "Stationery Sets", description: "Curated sets with rulers, erasers, sharpeners and more." },
  { icon: Backpack, title: "Bags & Cases", description: "Trendy backpacks and pencil cases to carry it all in style." },
];

const Index = () => {
  const [menuOpen, setMenuOpen] = useState(false);
  const [searchOpen, setSearchOpen] = useState(false);
  const { toast } = useToast();
  const [formData, setFormData] = useState({ name: "", email: "", message: "" });

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (!formData.name.trim() || !formData.email.trim() || !formData.message.trim()) {
      toast({ title: "Please fill all fields", variant: "destructive" });
      return;
    }
    toast({ title: "Message sent!", description: "We'll get back to you soon ✨" });
    setFormData({ name: "", email: "", message: "" });
  };

  return (
    <main className="min-h-screen">
      {/* ===== NAVBAR ===== */}
      <nav className="fixed top-0 left-0 right-0 z-50 bg-foreground/90 backdrop-blur-md border-b border-primary-foreground/10">
        <div className="max-w-7xl mx-auto px-6 py-3 flex items-center justify-between">
          <a href="#" className="flex items-center gap-2">
            <div className="w-9 h-9 rounded-full bg-primary flex items-center justify-center">
              <span className="text-primary-foreground font-display font-extrabold text-xl tracking-tight">Z</span>
            </div>
            <span className="font-display font-extrabold text-primary-foreground text-xl hidden sm:block tracking-tight">
              Zyra Study Store
            </span>
          </a>

          <ul className="hidden md:flex items-center gap-8 text-primary-foreground/70 text-sm font-medium">
            <li><a href="#" className="hover:text-primary transition-colors">Home</a></li>
            <li><a href="#categories" className="hover:text-primary transition-colors">Categories</a></li>
            <li><a href="#about" className="hover:text-primary transition-colors">About</a></li>
            <li><a href="#contact" className="hover:text-primary transition-colors">Contact</a></li>
          </ul>

          <div className="flex items-center gap-3">
            <AnimatePresence>
              {searchOpen && (
                <motion.input
                  initial={{ width: 0, opacity: 0 }}
                  animate={{ width: 180, opacity: 1 }}
                  exit={{ width: 0, opacity: 0 }}
                  transition={{ duration: 0.3 }}
                  type="text"
                  placeholder="Search..."
                  className="h-8 rounded-full bg-primary-foreground/10 border border-primary-foreground/20 px-3 text-sm text-primary-foreground placeholder:text-primary-foreground/40 focus:outline-none focus:border-primary"
                />
              )}
            </AnimatePresence>
            <button
              onClick={() => setSearchOpen(!searchOpen)}
              className="p-2 rounded-full hover:bg-primary-foreground/10 transition-colors text-primary-foreground/70 hover:text-primary"
            >
              <Search className="w-4 h-4" />
            </button>

            <div className="hidden md:flex items-center gap-1">
              <a href="#" className="p-2 rounded-full hover:bg-primary-foreground/10 transition-colors text-primary-foreground/50 hover:text-primary"><Instagram className="w-4 h-4" /></a>
              <a href="#" className="p-2 rounded-full hover:bg-primary-foreground/10 transition-colors text-primary-foreground/50 hover:text-primary"><Facebook className="w-4 h-4" /></a>
              <a href="#" className="p-2 rounded-full hover:bg-primary-foreground/10 transition-colors text-primary-foreground/50 hover:text-primary"><Twitter className="w-4 h-4" /></a>
            </div>

            <button
              onClick={() => setMenuOpen(!menuOpen)}
              className="md:hidden p-2 rounded-full hover:bg-primary-foreground/10 transition-colors text-primary-foreground/70"
            >
              {menuOpen ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
            </button>
          </div>
        </div>

        <AnimatePresence>
          {menuOpen && (
            <motion.div
              initial={{ height: 0, opacity: 0 }}
              animate={{ height: "auto", opacity: 1 }}
              exit={{ height: 0, opacity: 0 }}
              className="md:hidden overflow-hidden bg-foreground/95 border-t border-primary-foreground/10"
            >
              <ul className="flex flex-col items-center gap-4 py-6 text-primary-foreground/70 text-sm font-medium">
                <li><a href="#" onClick={() => setMenuOpen(false)} className="hover:text-primary transition-colors">Home</a></li>
                <li><a href="#categories" onClick={() => setMenuOpen(false)} className="hover:text-primary transition-colors">Categories</a></li>
                <li><a href="#about" onClick={() => setMenuOpen(false)} className="hover:text-primary transition-colors">About</a></li>
                <li><a href="#contact" onClick={() => setMenuOpen(false)} className="hover:text-primary transition-colors">Contact</a></li>
              </ul>
              <div className="flex items-center justify-center gap-4 pb-6">
                <a href="#" className="text-primary-foreground/50 hover:text-primary"><Instagram className="w-5 h-5" /></a>
                <a href="#" className="text-primary-foreground/50 hover:text-primary"><Facebook className="w-5 h-5" /></a>
                <a href="#" className="text-primary-foreground/50 hover:text-primary"><Twitter className="w-5 h-5" /></a>
              </div>
            </motion.div>
          )}
        </AnimatePresence>
      </nav>

      {/* ===== HERO SECTION ===== */}
      <section className="relative w-full h-screen overflow-hidden">
        <div className="absolute inset-0">
          <img src={heroBg} alt="Colorful school supplies arranged on a desk" className="w-full h-full object-cover" />
          <div className="absolute inset-0 bg-gradient-to-r from-foreground/80 via-foreground/50 to-transparent" />
        </div>

        <div className="relative z-10 flex flex-col justify-center h-full px-8 md:px-16 lg:px-24 max-w-3xl">
          <motion.div initial={{ opacity: 0, y: 30 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.8, ease: "easeOut" }}>
            <span className="inline-block px-4 py-1.5 rounded-full bg-primary/20 text-primary-foreground text-sm font-medium mb-6 backdrop-blur-sm border border-primary/30">
              ✨ Your Study Style Destination
            </span>
          </motion.div>

          <motion.h1
            className="text-5xl md:text-7xl font-extrabold text-primary-foreground leading-tight font-display"
            initial={{ opacity: 0, y: 40 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.2, ease: "easeOut" }}
          >
            Zyra Study
            <span className="block text-secondary">Store</span>
          </motion.h1>

          <motion.p
            className="mt-6 text-lg md:text-xl text-primary-foreground/80 max-w-lg leading-relaxed"
            initial={{ opacity: 0, y: 40 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.4, ease: "easeOut" }}
          >
            Welcome to Zyra Study Store — your one stop for stylish school essentials.
          </motion.p>

          <motion.div
            className="mt-10 flex gap-4"
            initial={{ opacity: 0, y: 40 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.6, ease: "easeOut" }}
          >
            <a href="#categories" className="px-8 py-3.5 rounded-full bg-primary text-primary-foreground font-semibold text-base hover:brightness-110 transition-all shadow-lg hover:shadow-xl">
              Shop Now
            </a>
            <a href="#about" className="px-8 py-3.5 rounded-full border-2 border-primary-foreground/30 text-primary-foreground font-semibold text-base hover:bg-primary-foreground/10 transition-all backdrop-blur-sm">
              Learn More
            </a>
          </motion.div>
        </div>

        <motion.div className="absolute bottom-8 left-1/2 -translate-x-1/2" animate={{ y: [0, 10, 0] }} transition={{ duration: 2, repeat: Infinity }}>
          <div className="w-6 h-10 rounded-full border-2 border-primary-foreground/40 flex items-start justify-center p-1.5">
            <div className="w-1.5 h-3 rounded-full bg-primary-foreground/60" />
          </div>
        </motion.div>
      </section>

      {/* ===== CATEGORIES SECTION ===== */}
      <section id="categories" className="py-24 px-8 md:px-16 lg:px-24 bg-background">
        <div className="max-w-6xl mx-auto">
          <motion.div className="text-center mb-16" initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} transition={{ duration: 0.6 }}>
            <span className="text-primary font-semibold text-sm tracking-widest uppercase">What We Offer</span>
            <h2 className="text-4xl md:text-5xl font-bold text-foreground mt-3 font-display">Shop by Category</h2>
          </motion.div>

          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
            {categories.map((cat, i) => (
              <motion.div
                key={cat.title}
                className="group relative bg-card rounded-2xl p-8 text-center border border-border hover:border-primary/30 transition-all duration-300"
                style={{ boxShadow: "var(--card-shadow)" }}
                initial={{ opacity: 0, y: 40 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.5, delay: i * 0.1 }}
                whileHover={{ y: -6, boxShadow: "var(--card-hover-shadow)" }}
              >
                <div className="w-16 h-16 mx-auto mb-5 rounded-2xl bg-primary/10 flex items-center justify-center group-hover:bg-primary/20 transition-colors">
                  <cat.icon className="w-7 h-7 text-primary" />
                </div>
                <h3 className="text-lg font-bold text-foreground font-display mb-2">{cat.title}</h3>
                <p className="text-muted-foreground text-sm leading-relaxed">{cat.description}</p>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      {/* ===== ABOUT SECTION ===== */}
      <section id="about" className="py-24 px-8 md:px-16 lg:px-24 bg-muted/50">
        <div className="max-w-4xl mx-auto text-center">
          <motion.div initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} transition={{ duration: 0.6 }}>
            <span className="text-primary font-semibold text-sm tracking-widest uppercase">About Us</span>
            <h2 className="text-4xl md:text-5xl font-bold text-foreground mt-3 font-display">Why Zyra Study Store?</h2>
            <p className="mt-6 text-muted-foreground text-lg leading-relaxed max-w-2xl mx-auto">
              We believe that school supplies should be as fun and inspiring as learning itself.
              Zyra Study Store brings you the trendiest, most colorful stationery that makes
              studying feel like a creative adventure. From pastel highlighters to aesthetic
              notebooks — we've got everything to make your school life stylish.
            </p>
          </motion.div>

          <motion.div
            className="mt-16 grid grid-cols-1 md:grid-cols-3 gap-10"
            initial={{ opacity: 0, y: 30 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.6, delay: 0.2 }}
          >
            {[
              { value: "500+", label: "Products" },
              { value: "2K+", label: "Happy Students" },
              { value: "100%", label: "Stylish Picks" },
            ].map((stat) => (
              <div key={stat.label}>
                <div className="text-5xl font-extrabold text-primary font-display">{stat.value}</div>
                <div className="mt-2 text-muted-foreground font-medium">{stat.label}</div>
              </div>
            ))}
          </motion.div>
        </div>
      </section>

      {/* ===== CONTACT SECTION ===== */}
      <section id="contact" className="py-20 px-8 bg-muted/50">
        <div className="max-w-6xl mx-auto">
          <motion.div className="text-center mb-14" initial={{ opacity: 0, y: 20 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} transition={{ duration: 0.6 }}>
            <span className="inline-block px-4 py-1.5 rounded-full bg-primary/10 text-primary text-sm font-medium mb-4">Get In Touch</span>
            <h2 className="text-4xl md:text-5xl font-display font-bold text-foreground">Contact Us</h2>
            <p className="mt-4 text-muted-foreground max-w-lg mx-auto">Have questions? We'd love to hear from you. Reach out anytime!</p>
          </motion.div>

          <div className="grid md:grid-cols-2 gap-12">
            <motion.div className="space-y-8" initial={{ opacity: 0, x: -30 }} whileInView={{ opacity: 1, x: 0 }} viewport={{ once: true }} transition={{ duration: 0.6 }}>
              <div className="flex items-start gap-4">
                <div className="w-12 h-12 rounded-2xl bg-primary/10 flex items-center justify-center shrink-0"><Mail className="w-5 h-5 text-primary" /></div>
                <div>
                  <h3 className="font-display font-semibold text-foreground text-lg">Email Us</h3>
                  <p className="text-muted-foreground mt-1">hello@zyrastudystore.com</p>
                </div>
              </div>
              <div className="flex items-start gap-4">
                <div className="w-12 h-12 rounded-2xl bg-secondary/20 flex items-center justify-center shrink-0"><Phone className="w-5 h-5 text-secondary-foreground" /></div>
                <div>
                  <h3 className="font-display font-semibold text-foreground text-lg">Call Us</h3>
                  <p className="text-muted-foreground mt-1">+1 (555) 123-4567</p>
                </div>
              </div>
              <div className="flex items-start gap-4">
                <div className="w-12 h-12 rounded-2xl bg-accent/10 flex items-center justify-center shrink-0"><MapPin className="w-5 h-5 text-accent" /></div>
                <div>
                  <h3 className="font-display font-semibold text-foreground text-lg">Visit Us</h3>
                  <p className="text-muted-foreground mt-1">123 Study Lane, School District</p>
                </div>
              </div>
            </motion.div>

            <motion.form onSubmit={handleSubmit} className="bg-card rounded-2xl p-8 shadow-lg space-y-5" initial={{ opacity: 0, x: 30 }} whileInView={{ opacity: 1, x: 0 }} viewport={{ once: true }} transition={{ duration: 0.6 }}>
              <div>
                <label className="text-sm font-medium text-foreground mb-1.5 block">Name</label>
                <input type="text" maxLength={100} value={formData.name} onChange={(e) => setFormData({ ...formData, name: e.target.value })} placeholder="Your name" className="w-full h-11 rounded-xl border border-input bg-background px-4 text-sm focus:outline-none focus:ring-2 focus:ring-primary/30 focus:border-primary transition-all" />
              </div>
              <div>
                <label className="text-sm font-medium text-foreground mb-1.5 block">Email</label>
                <input type="email" maxLength={255} value={formData.email} onChange={(e) => setFormData({ ...formData, email: e.target.value })} placeholder="your@email.com" className="w-full h-11 rounded-xl border border-input bg-background px-4 text-sm focus:outline-none focus:ring-2 focus:ring-primary/30 focus:border-primary transition-all" />
              </div>
              <div>
                <label className="text-sm font-medium text-foreground mb-1.5 block">Message</label>
                <textarea maxLength={1000} value={formData.message} onChange={(e) => setFormData({ ...formData, message: e.target.value })} placeholder="How can we help?" rows={4} className="w-full rounded-xl border border-input bg-background px-4 py-3 text-sm focus:outline-none focus:ring-2 focus:ring-primary/30 focus:border-primary transition-all resize-none" />
              </div>
              <button type="submit" className="w-full h-11 rounded-xl bg-primary text-primary-foreground font-semibold text-sm hover:brightness-110 transition-all flex items-center justify-center gap-2">
                Send Message <Send className="w-4 h-4" />
              </button>
            </motion.form>
          </div>
        </div>
      </section>

      {/* ===== FOOTER ===== */}
      <footer className="bg-foreground pt-14 pb-8 px-8">
        <div className="max-w-6xl mx-auto">
          <div className="grid sm:grid-cols-2 md:grid-cols-4 gap-10 mb-12">
            <div>
              <div className="flex items-center gap-2 mb-4">
                <div className="w-8 h-8 rounded-full bg-primary flex items-center justify-center">
                  <span className="text-primary-foreground font-display font-extrabold text-xl tracking-tight">Z</span>
                </div>
                <span className="font-display font-extrabold text-primary-foreground text-xl tracking-tight">Zyra Study Store</span>
              </div>
              <p className="text-primary-foreground/50 text-sm leading-relaxed">Your one stop for stylish school essentials. Making studying fun and fashionable.</p>
            </div>

            <div>
              <h4 className="font-display font-semibold text-primary-foreground mb-4">Quick Links</h4>
              <ul className="space-y-2 text-sm text-primary-foreground/50">
                <li><a href="#" className="hover:text-primary transition-colors">Home</a></li>
                <li><a href="#categories" className="hover:text-primary transition-colors">Categories</a></li>
                <li><a href="#about" className="hover:text-primary transition-colors">About</a></li>
                <li><a href="#contact" className="hover:text-primary transition-colors">Contact</a></li>
              </ul>
            </div>

            <div>
              <h4 className="font-display font-semibold text-primary-foreground mb-4">Contact</h4>
              <ul className="space-y-3 text-sm text-primary-foreground/50">
                <li className="flex items-center gap-2"><Mail className="w-4 h-4 text-primary" /> hello@zyrastudystore.com</li>
                <li className="flex items-center gap-2"><Phone className="w-4 h-4 text-primary" /> +1 (555) 123-4567</li>
              </ul>
            </div>

            <div>
              <h4 className="font-display font-semibold text-primary-foreground mb-4">Follow Us</h4>
              <div className="flex gap-3">
                <a href="#" className="w-9 h-9 rounded-full bg-primary-foreground/10 flex items-center justify-center text-primary-foreground/50 hover:bg-primary hover:text-primary-foreground transition-all"><Instagram className="w-4 h-4" /></a>
                <a href="#" className="w-9 h-9 rounded-full bg-primary-foreground/10 flex items-center justify-center text-primary-foreground/50 hover:bg-primary hover:text-primary-foreground transition-all"><Facebook className="w-4 h-4" /></a>
                <a href="#" className="w-9 h-9 rounded-full bg-primary-foreground/10 flex items-center justify-center text-primary-foreground/50 hover:bg-primary hover:text-primary-foreground transition-all"><Twitter className="w-4 h-4" /></a>
                <a href="#" className="w-9 h-9 rounded-full bg-primary-foreground/10 flex items-center justify-center text-primary-foreground/50 hover:bg-primary hover:text-primary-foreground transition-all"><Youtube className="w-4 h-4" /></a>
              </div>
            </div>
          </div>

          <div className="border-t border-primary-foreground/10 pt-6 text-center">
            <p className="text-sm text-primary-foreground/40 flex items-center justify-center gap-1">
              Made with <Heart className="w-4 h-4 text-primary fill-primary" /> for stylish students · © 2026 Zyra Study Store
            </p>
          </div>
        </div>
      </footer>
    </main>
  );
};

export default Index;











