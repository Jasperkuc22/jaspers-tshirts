import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

const products = [
  { id: 1, name: "T-Shirt 1", description: "A super comfy t-shirt for everyday wear." },
  { id: 2, name: "T-Shirt 2", description: "A stylish option for any outfit." },
  { id: 3, name: "T-Shirt 3", description: "Cool design with a relaxed fit." }
];

export default function Home() {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  const handleCheckout = () => {
    alert("Checkout coming soon! Total items: " + cart.length);
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-[#fffaf0] via-[#fdf6e3] to-[#f5f5dc] p-4">
      <header className="text-center py-10">
        <h1 className="text-4xl font-bold tracking-tight">Jasper's T-Shirts</h1>
        <p className="text-lg text-muted-foreground mt-2">Cool shirts. Cooler vibes.</p>
        <div className="mt-4 space-x-4">
          <Button onClick={handleCheckout}>Checkout ({cart.length})</Button>
          <Button variant="outline" onClick={() => alert("Contact us at hello@jaspertees.com")}>Contact</Button>
        </div>
      </header>

      <main className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 max-w-6xl mx-auto">
        {products.map((product) => (
          <Card key={product.id} className="bg-[#fefcea] rounded-2xl shadow-md">
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-2">{product.name}</h2>
              <p className="text-sm text-muted-foreground mb-4">{product.description}</p>
              <Button onClick={() => addToCart(product)}>Add to Cart</Button>
            </CardContent>
          </Card>
        ))}
      </main>
    </div>
  );
}
