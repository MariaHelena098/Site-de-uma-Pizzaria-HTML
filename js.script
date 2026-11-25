document.addEventListener('DOMContentLoaded', function() {
    const form = document.getElementById('form-pedido');
    const spanTotal = document.getElementById('valor-total');

    // Função para calcular o preço total
    function calcularTotal() {
        let total = 0;
        
        // Pega todos os checkboxes e radios selecionados com o atributo data-preco
        const selecionados = form.querySelectorAll('input[type="checkbox"]:checked, input[type="radio"]:checked');
        
        selecionados.forEach(el => {
            const preco = parseFloat(el.getAttribute('data-preco')) || 0;
            total += preco;
        });

        // Formata o valor para o padrão monetário brasileiro (R$ 0,00)
        spanTotal.textContent = `R$ ${total.toFixed(2).replace('.', ',')}`;
    }

    // Atualiza sempre que houver mudança em qualquer campo do formulário
    form.addEventListener('change', calcularTotal);

    // Ação ao enviar o pedido
    form.addEventListener('submit', function(e) {
        e.preventDefault();

        const nome = document.getElementById('Nm').value.trim();
        const endereco = document.getElementById('End').value.trim();
        const pagamento = document.getElementById('pagamento').value;
        
        // Validação: Verifica se o nome e o endereço foram preenchidos
        if (!nome || !endereco) {
            alert('Por favor, preencha seu nome e endereço de entrega!');
            return;
        }

        // Validação: Verifica se ao menos uma pizza foi selecionada
        const pizzas = form.querySelectorAll('input[name="PizzaSalgada"]:checked, input[name="PizzaDoce"]:checked');
        if (pizzas.length === 0) {
            alert('Por favor, selecione pelo menos uma pizza para o seu pedido!');
            return;
        }

        // Mensagem de sucesso
        alert(`Obrigado pelo pedido, ${nome}!\n\nSeu pedido foi registrado com sucesso e será entregue em:\n${endereco}.\n\nForma de pagamento: ${pagamento}\nTotal: ${spanTotal.textContent}\n\nBom apetite! 🍕`);
        
        // Reseta o formulário e recalcula o total para zero
        form.reset();
        calcularTotal();
    });

    // Executa o cálculo ao carregar a página (caso venha algo marcado por padrão)
    calcularTotal();
});
