<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>{{ page_title }}</title>
    {{ content_for_header }}
</head>
<body>
    {{ content_for_layout }}
</body>
</html>
{% comment %} Safira Tech Style - Página de Productos {% endcomment %}

{% layout "theme" %}

<style>
  body {
    background-color: black;
    color: white;
    font-family: Arial, sans-serif;
    text-align: center;
  }
  .header {
    font-size: 2rem;
    font-weight: bold;
    color: #00bfff;
    margin-bottom: 20px;
  }
  .product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 20px;
  }
  .product-card {
    background: #1a1a1a;
    border: 2px solid #00bfff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px #00bfff;
  }
  .product-title {
    font-size: 1.5rem;
    color: #00bfff;
  }
  .product-price {
    font-size: 1.2rem;
    color: #ccc;
  }
  .buy-button {
    display: block;
    background: #00bfff;
    color: black;
    padding: 10px;
    margin-top: 10px;
    text-decoration: none;
    border-radius: 5px;
  }
  .buy-button:hover {
    background: #009acd;
  }
</style>

<div class="header">SAFIRA TECH STYLE</div>
<p>Tecnología con Estilo - Encuentra los mejores accesorios tech</p>

<div class="product-grid">
  {% for product in collections["all"].products %}
    <div class="product-card">
      <img src="{{ product.featured_image | img_url: 'medium' }}" alt="{{ product.title }}" style="width:100%; border-radius: 10px;">
      <h2 class="product-title">{{ product.title }}</h2>
      <p class="product-price">{{ product.price | money }}</p>
      <a href="{{ product.url }}" class="buy-button">Comprar Ahora</a>
    </div>
  {% endfor %}
</div>
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
